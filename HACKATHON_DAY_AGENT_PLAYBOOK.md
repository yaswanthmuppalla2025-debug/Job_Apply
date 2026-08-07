# Hack2Hire AI Agent Playbook

> Consolidated from the 20 supplied screenshots into one hackathon-day command center. Every unique instruction is retained; only exact screenshot overlap is deduplicated. The material is reorganized into paste-ready prompts and quick-reference sections.

## How to use this file on hackathon day

1. Read the challenge and choose the pattern using [Pattern selection](#pattern-selection-decide-in-the-first-30-seconds-of-reading-the-problem).
2. Paste the [system prompt](#system-prompt--paste-this-to-your-ai-agent-at-the-start-of-the-hackathon) into the AI agent at the start.
3. Give the agent the actual challenge requirements.
4. Paste the [scaffold skill](#scaffold-skill--paste-this-to-the-ai-agent-to-generate-the-project-skeleton) to generate the project skeleton.
5. Finish Layer 1 before adding agents, routing, deployment, or production extensions.
6. Use [what to change for a new problem](#on-hackathon-day--what-to-change-for-a-new-problem) as the domain-adaptation checklist.
7. Use the implemented/deferred lists to explain deliberate tradeoffs during the defense.

---

# SYSTEM PROMPT — Paste this to your AI agent at the START of the hackathon

## Context

I'm in a 3-hour Hack2Hire challenge for Lead Applied AI Engineer II at Deloitte. I need to build an end-to-end AI application and demo it, then defend my decisions in a 1-hour call.

## Tech Stack (locked)

- **FastAPI** — API/backend
- **SQLite** — metadata, state, records
- **ChromaDB** — vector store for RAG
- **Unstructured** — document parsing (PDF, docx, email, txt)
- **LangChain** — RAG plumbing, LLM calls, structured output, memory
- **Azure OpenAI** — LLM (gpt-4) + embeddings (text-embedding-ada-002), keys provided
- **LangGraph** — multi-agent orchestration (only if time permits)
- **Streamlit** — UI (chat + file upload)
- **Docker** — containerize for deployment (nice-to-have)
- **pytesseract + Pillow** — OCR fallback if scanned documents

## Coding Playbook (enforce on ALL generated code)

### Naming

- Files, functions, variables: `snake_case` — `extract_risks.py`, `def make_risks_node()`, `client_needs`
- Classes: `PascalCase` — `RisksResult`, `MCPToolClient`, `AbstractLLMAdapter`
- Constants: `UPPER_SNAKE` — `MAX_RETRIES`, `CONFIDENCE_THRESHOLD`
- Async methods: prefix with `a` — `ainvoke_text()`, `acall_tool()`, `aget_state()`
- Factory functions: prefix with `make_` — `make_retrieve_node()`, `make_needs_node()`
- Interfaces: prefix with `Abstract` — `AbstractLLMAdapter`, `AbstractToolClient`
- Private: single underscore — `_create_llm()`, `_SCHEMA_REGISTRY`

### Type hints (mandatory everywhere)

```python
def make_needs_node(
    llm: AbstractLLMAdapter,
    prompts: AbstractPromptRegistry,
) -> Callable:
    ...

async def ainvoke_text(
    self,
    messages: list[dict],
    schema_hint: dict | None = None,
) -> str:
    ...

def save(self, tenant_id: str, artifact: BaseModel) -> str:
    ...
```

### Pydantic v2 patterns

- Output schemas: `class NeedsResult(BaseModel)` with typed fields — `client_needs: list[str]`
- Graph state: `class PursuitState(TypedDict, total=False)` — **NOT Pydantic** (LangGraph requirement)
- Validation: `model_validate_json(text)` for LLM output, `model_dump()` for serialization
- Never `dict()` — always `.model_dump()`
- Never `parse_raw()` — always `.model_validate_json()`

### Imports

- All imports at file top, never inside functions (except lazy imports in DI containers)
- Group: stdlib → third-party → local. One blank line between groups
- Logging: `from shared.logging import get_logger` — never `import logging`
- Exceptions: raise from `shared.exceptions` — never bare `raise Exception("...")`

### Error handling

- Adapters: catch specific errors (`ValidationError`, `ConnectionError`), let unknown errors bubble up
- Specialist nodes: wrap in `try/except`, return empty result on failure (graceful degradation)
- API: global `@app.exception_handler(AppError)` converts errors to structured JSON
- Never catch bare `Exception` in adapters — only at the specialist-node top level

### DI pattern

- One `container.py` per module using `dependency_injector.DeclarativeContainer`
- `providers.Singleton` for stateless services; `providers.Factory` for per-request objects
- Singletons must be stateless — no mutable instance variables

---

## Scaffold Skill — Paste this to the AI agent to generate the project skeleton

Create a Python project with this exact structure. Every folder gets `__init__.py`.

```text
ui/                 ← Streamlit frontend. Only talks to API via HTTP.
api/                ← FastAPI. Routes requests. No business logic.
agents/             ← LLM orchestration. Split into core/ + {domain}/. See agents/ section below.
mcp_tools/          ← MCP server with retrieval tools. Read-only, no ingestion.
file_processing/    ← Ingestion pipeline: parse → chunk → embed → store. Write-only, no retrieval.
shared/             ← Config, logging, exceptions ONLY. No domain logic.
tests/
data/
```

Rules:

- Hexagonal architecture: `interfaces/` (ABC), `adapters/` (concrete), `repositories/` (persistence)
- Every module has `container.py` with dependency-injector `DeclarativeContainer`
- All code: `snake_case` files/functions, `PascalCase` classes, type hints on every function
- Pydantic v2 for all data models, `TypedDict` for LangGraph state
- All LLM/MCP/DB calls must be `async def`
- `from shared.logging import get_logger` — never raw logging
- `from shared.exceptions import AppError` hierarchy — never bare Exception
- Flow: UI → API → Agents → MCP Tools. File Processing feeds the vector store. No skipping layers.

---

# Architecture Pattern — Layered Build

Build in layers. Each layer is a working demo. Never rewrite, only extend.

## Layer 1 (first 90 min — MUST finish)

- RAG pipeline: parse docs → chunk → embed → store in ChromaDB
- Single LLM call with structured output (Pydantic schema)
- Streamlit UI: file upload + display results
- FastAPI endpoint backing it

## Layer 2 (next 60 min — if time)

- Split single LLM call into specialized agents (one per output field)
- LangGraph `StateGraph` orchestrates them
- Fan-out to agents → merge results → same output schema

## Layer 3 (last 30 min — nice-to-have)

- Add router/classifier before agents
- Only invoke relevant agents based on query type
- Reduces latency for targeted questions

## Pattern Selection (decide in the first 30 seconds of reading the problem)

- User uploads documents and waits for a report? → **Batch fan-out** (multi-agent OK)
- User chats in real time? → **Conversational** (single agent + memory + streaming, NO multi-agent)
- User submits and expects a routed action? → **Triage** (classify → one agent)

---

# Project Structure

Monorepo with clear boundaries. Each folder can become its own service later.

- **`ui/`** → Streamlit frontend. Only talks to API.
- **`api/`** → FastAPI. Single entry point. Coordinates everything. No business logic here.
- **`agents/`** → LLM logic, prompts, orchestration. Called by API.
- **`mcp_tools/`** → Retrieval tools (vector search, DB queries). Called by agents via MCP (`stdio`).
- **`file_processing/`** → Document parsing, chunking, embedding, storing. Called by API on upload.
- **`shared/`** → Schemas, config, common utilities. Imported by everyone.
- **`tests/`** → All tests.
- **`data/`** → Uploaded documents, sample data.

Flow: UI → API → Agents → MCP Tools. File Processing feeds data into the vector store. No skipping layers.

## Rules & Boundaries

1. Get end-to-end working first (Layer 1) before anything else.
2. Every layer must be demo-able standalone.
3. No rewrites between layers — only add new modules.

## Hexagonal architecture — enforce on every module

```text
module/
├── models/          ← Pydantic domain objects
├── interfaces/      ← ABC ports (contracts)
├── adapters/        ← External API calls (Azure, LangChain, file I/O)
├── repositories/    ← DB/storage persistence (ChromaDB, SQLite)
├── services/        ← Business logic (depends ONLY on interfaces)
└── container.py     ← dependency-injector DeclarativeContainer with providers.Singleton
```

### Global rules

- Services depend on interfaces, **NEVER** on concrete adapters/repositories.
- All imports at the top of files, never inside functions.
- Logging: always `from shared.logging import get_logger` — never raw `logging.getLogger()`.
- Exceptions: always raise from `shared.exceptions` hierarchy (`AppError` → `ValidationError | IngestionError | RetrievalError | TenantError`). API has a global handler that converts them to structured JSON responses.

### `shared/`

- Infrastructure only: config, exceptions, logging. **NO** domain logic, **NO** domain models.
- Every module can import from `shared`. `shared` imports from nobody.

### `file_processing/`

- Ingestion only: parse, chunk, `embed_documents`, store. **NO** retrieval methods.
- Interfaces are write-only. No search, no `embed_query` here.
- Return a result model from `ingest()`, not a bare int.
- **Implemented:** file validation (type/size/empty), deduplication (`delete_by_source` before re-store), `IngestionResult` model, SQLite ingestion history tracking.
- **Deferred (mention in defense):** async background processing, PII redaction (Microsoft Presidio), multi-tenancy tagging, retry/circuit breaker on embedding API, semantic/hierarchical chunking strategies, spaCy NER for better metadata extraction during retrieval, embedding model versioning.

### `mcp_tools/`

- Retrieval only: `embed_query`, search, retrieve. **NO** ingestion methods.
- Owns its own interfaces, models, and adapters. Does not import `file_processing` interfaces.
- MCP SDK (v2.0): `from mcp.server.mcpserver import MCPServer` (`FastMCP` was removed in v2).
- Tool annotations: all tools marked `read_only_hint=True, idempotent_hint=True` — tells the agent they are safe to retry and have no side effects.

#### MCP primitives (protocol concepts)

| Primitive | Purpose | Status |
|---|---|---|
| Tools | Actions the agent can call (search, list, get_chunks) | ✅ Implemented |
| Resources | Static data the agent can browse declaratively | Deferred |
| Prompts | Reusable prompt templates discoverable via protocol | Deferred |

#### Deferred (mention in defense)

- Streamable HTTP transport — one config swap to expose MCP over the network as a microservice.
- MCP Resources — agents browse document metadata declaratively; reduces token cost versus tool calls.
- MCP Prompts — version-controlled prompt templates agents discover at runtime.
- Why MCP over REST — protocol-level tool discovery via `list_tools()`, transport-agnostic (`stdio` → HTTP with zero code change).
- Tool annotations — `read_only_hint`, `idempotent_hint`, `destructive_hint` tell the agent retry safety and side-effect behavior.
- Prompt-injection defense — output guardrails (LLM Guard / Azure AI Content Safety / Bedrock Guardrails) scan tool results before feeding them to the LLM.
- Testability — call `await mcp.call_tool()` directly without transport; unit tests mock the DI container; integration tests use in-memory ChromaDB.
- Crash recovery — `stdio`: MCP client reconnects. HTTP: load balancer + health checks. `SIGTERM` graceful drain.
- Auth/RBAC — JWT validation on HTTP transport, per-tool access control by role.
- Rate limiting / circuit breaker — protect embedding API from burst traffic; fail gracefully.
- Tool-result caching — TTL-based cache on repeated queries; cuts latency and API cost.
- OpenTelemetry tracing — correlate agent request → tool call → vector query end-to-end (SDK already ships `opentelemetry-api`).
- Input validation — cap `top_k`, reject empty queries, Pydantic on tool arguments at the boundary.
- Pagination — cursor-based for `list_documents` at scale (100K+ documents).
- Context-window awareness — `max_tokens` parameter so returned chunks do not blow the LLM context.
- Contextual compression — one LLM call per chunk to extract only query-relevant sentences before feeding them to the agent (reduces noise, saves tokens at scale).
- Hybrid search — BM25 + vector fusion catches exact keyword matches semantic search misses.
- PII filtering — Microsoft Presidio on tool outputs before returning them to the LLM.
- Tool versioning — schema changes do not break agents pinned to older versions.
- Usage analytics — structured tool-call events → observability pipeline (Datadog/CloudWatch).

### `agents/`

- LLM orchestration and prompts. Calls `mcp_tools` for retrieval, never `file_processing` directly.
- Split into `core/` (reusable) and `{domain}/` (customizable). Structure is in the Scaffold Skill above.

#### On hackathon day — what to change for a new problem

1. `models/` — new `TypedDict` state, new output Pydantic model, new specialist schemas.
2. `nodes/specialists/` — one async node per output field (copy template, change prompt + schema).
3. `prompts/` — write extraction/synthesis prompts for the domain.
4. `repositories/` — new SQLite table schema for final output.
5. `orchestrator/` — adjust fan-out edges if there are more/fewer specialists.
6. `container.py` — register new schemas in `_create_llm()`.

#### Agent pattern choice (decide based on problem)

| Pattern | When | Example |
|---|---|---|
| Single Agent + Structured Output | Known output schema, extraction task | ✅ Our pursuit brief |
| ReAct (reason-act-observe) | Open-ended exploration | Overkill for extraction |
| Multi-Agent Fan-Out (LangGraph) | Each field needs specialized reasoning | Layer 2 upgrade |
| Plan-and-Execute | Complex sequential dependencies | Over-engineering |
| Router/Triage | Multiple query types | Different problem |

#### Enterprise patterns implemented

- HITL interrupt — compliance requirement; human reviews before final output.
- Node-level retry — extraction retries 2x with feedback if the LLM returns empty fields.
- Streaming callback — pluggable event emitter (`node_start/end/error/interrupt`).
- Persistent checkpointing — resume from crash, time-travel to any node.
- Conditional branching — skip synthesis on low confidence.

---

# Async Patterns (for any LangGraph + FastAPI app)

**Rule:** All graph nodes must be `async def` so LangGraph fan-out uses `asyncio.gather()` instead of `ThreadPoolExecutor`. API endpoints use `await graph.ainvoke()` to avoid blocking the event loop.

**Interface naming convention:** async methods are prefixed with `a` — `ainvoke()`, `acall_tool()`, `ainvoke_text()`, `aget_state()`.

**Trace decorator pattern:** use `asyncio.iscoroutinefunction(func)` to auto-detect sync/async — one decorator handles both.

**MCP in-process:** MCP SDK tools are natively async. Call `await mcp.call_tool()` directly — no `nest_asyncio` or `run_until_complete` is needed when already inside an event loop.

**Checkpointer options:**

- `InMemorySaver` — async-native, zero-config, state lost on restart (fine for demo).
- `AsyncSqliteSaver` — persistent; needs an async context manager via FastAPI lifespan.
- `AsyncPostgresSaver` — multi-worker, shared state (production).

## Async Pitfalls (tell your AI agent these rules)

### Concurrency traps

- Never `asyncio.run()` inside uvicorn — the event loop is already running and this causes `RuntimeError`.
- Never `time.sleep()` in async code — it blocks the entire event loop; use `await asyncio.sleep()`.
- Singletons must be stateless — parallel async nodes share them, so mutable state creates a race condition.
- Pass context through parameters, not instance variables — thread-safe by design.
- Use `try/except` in every specialist node — one failure in fan-out should not kill the graph.
- Four parallel LLM calls can trigger 429 rate limits — use `asyncio.Semaphore` to cap concurrency.
- Do not use `run_in_executor()` unless necessary — `contextvars` (correlation IDs) do not propagate to threads.

### SQLite under async

The single-writer lock means concurrent `save()` calls can produce `database is locked`. Fine for the demo; use a connection pool in production.

### Blocking I/O in async endpoints

`open()` and `shutil.copyfileobj()` briefly block the event loop. Use `aiofiles` for production. Acceptable for the hackathon.

### Coding standards

- All external calls (LLM, MCP, DB) must be `async def`.
- Pydantic models at all boundaries — API in/out, graph state, LLM output.
- Log format: `logger.info("msg %s", var)`, not f-strings (prevents log injection).
- Catch specific errors in adapters; let unexpected ones bubble up.

### Deferred (mention in defense)

- Multi-agent fan-out — specialized sub-agents per field (`NeedsExtractor`, `RiskAnalyzer`) via LangGraph subgraphs.
- LangGraph streaming modes (`values`, `updates`, `messages`) — stream partial results to the UI in real time.
- LangGraph Store — cross-thread long-term memory (agent remembers past briefs for the same client).
- Parallel nodes — fan-out `extract_needs` + `extract_risks` simultaneously, then fan-in results.
- Agent Gateway / Router — intent classification routes to the right orchestration (pursuit vs research vs risk).
- Model fallback chain — OpenAI fails → Anthropic → Azure OpenAI → graceful error.
- Cost controls — per-tenant token budgets, kill switch on runaway loops.
- Audit trail — immutable log of every LLM call (input, output, tokens, cost, model version).
- Agent Registry / Catalog — central registry of all agents with capabilities, SLAs, ownership.
- Prompt A/B testing — run v1 and v2 simultaneously; measure quality difference.
- Evaluation pipeline — golden test set + LLM-as-judge quality gate before deploying prompt changes.
- Feedback loop — user thumbs up/down → evaluation dataset → prompt-improvement cycle.
- Blue/Green deployment — deploy a new agent version alongside the old one, then gradually shift traffic.
- A2A protocol — Google's Agent-to-Agent protocol for cross-service agent communication.
- Secrets management — API keys in AWS Secrets Manager/Vault, not `.env` files.

### `api/`

- Routing only. Calls the `file_processing` container for uploads and agents for queries. No business logic.

### `ui/`

- Talks to API only via HTTP. Never imports from any other module.

---

# 3-Hour Execution Checklist

## First 30 seconds

- [ ] Identify the interaction shape: batch report, conversation, or routed action.
- [ ] Select Batch fan-out, Conversational, or Triage.
- [ ] Define the smallest structured output schema.

## Layer 1 — first 90 minutes

- [ ] Parse → chunk → embed → ChromaDB.
- [ ] Complete one structured LLM call using a Pydantic schema.
- [ ] Expose it through FastAPI.
- [ ] Upload and display through Streamlit.
- [ ] Preserve UI → API → Agent → MCP Tools and File Processing → vector-store boundaries.
- [ ] Make the layer independently demo-able.

## Layer 2 — next 60 minutes, only if Layer 1 works

- [ ] Split output fields into specialized agents.
- [ ] Add LangGraph `StateGraph` fan-out/fan-in.
- [ ] Keep the same output schema so Layer 1 is extended, not rewritten.

## Layer 3 — final 30 minutes, only if time remains

- [ ] Add router/classifier.
- [ ] Invoke only relevant agents.
- [ ] Add Docker or another nice-to-have only after the complete demo works.

## Before the demo and defense

- [ ] Confirm all graph, LLM, MCP, and DB calls follow the async rules.
- [ ] Confirm Pydantic models protect every boundary.
- [ ] Confirm specialist failures degrade gracefully.
- [ ] Demonstrate the working layer before describing deferred production extensions.
- [ ] Explain implemented versus deferred MCP, agent, scaling, security, evaluation, and observability choices.

---

## Transcription fidelity note

- Photos 8 and 20 are duplicates; photos 9 and 19 are duplicates; photos 10 and 17 are duplicates. Those exact copies are represented once.
- Screenshot overlaps were merged without removing intentionally repeated rules in separate contexts.
- A mobile overlay partially covered the beginning of the MCP testability bullet. Its complete substance was reconstructed from the visible continuation: direct `mcp.call_tool()` testing without transport, mocked DI for unit tests, and in-memory ChromaDB for integration tests.
- Obvious spelling and Markdown formatting issues were normalized for readability without changing the instructions.
