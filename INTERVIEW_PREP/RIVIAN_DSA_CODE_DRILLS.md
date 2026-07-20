# Rivian DSA Code Drills

Date: 2026-06-23
Target: Rivian Sr. AI Engineer, Enterprise Applied AI
Language: Python 3

Use this as a fast pattern-to-code recall sheet. For each problem:

1. Read the statement.
2. Say the trigger out loud.
3. Read the code once.
4. Say the time and space complexity.
5. Re-code only the high-priority ones if time is short.

## A. Hash Map / Frequency / Prefix State

Trigger: fast lookup, pairs, counts, "seen before", prefix sums, grouping.

### A1. Two Sum

Problem statement:
Given an integer array `nums` and an integer `target`, return indices of two numbers such that they add up to `target`. Assume exactly one solution and do not use the same element twice.

Pattern recognition:
For each number, ask "have I already seen the complement?"

```python
def two_sum(nums, target):
    seen = {}

    for i, x in enumerate(nums):
        need = target - x
        if need in seen:
            return [seen[need], i]
        seen[x] = i

    return []
```

Complexity: Time O(n), Space O(n)

### A2. Group Anagrams

Problem statement:
Given a list of strings, group the anagrams together.

Pattern recognition:
Strings belong together if they have the same character frequency.

```python
from collections import defaultdict


def group_anagrams(strs):
    groups = defaultdict(list)

    for word in strs:
        count = [0] * 26
        for ch in word:
            count[ord(ch) - ord("a")] += 1
        groups[tuple(count)].append(word)

    return list(groups.values())
```

Complexity: Time O(n*k), Space O(n*k), where k is average string length.

### A3. Top K Frequent Elements

Problem statement:
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements.

Pattern recognition:
Count first, then keep only the top k.

```python
from collections import Counter
import heapq


def top_k_frequent(nums, k):
    freq = Counter(nums)
    heap = []

    for num, count in freq.items():
        heapq.heappush(heap, (count, num))
        if len(heap) > k:
            heapq.heappop(heap)

    return [num for count, num in heap]
```

Complexity: Time O(n log k), Space O(n)

### A4. Subarray Sum Equals K

Problem statement:
Given an integer array `nums` and an integer `k`, return the number of continuous subarrays whose sum equals `k`.

Pattern recognition:
If current prefix is `p`, a previous prefix `p - k` gives a subarray sum of k.

```python
from collections import defaultdict


def subarray_sum(nums, k):
    prefix_counts = defaultdict(int)
    prefix_counts[0] = 1

    prefix = 0
    answer = 0

    for x in nums:
        prefix += x
        answer += prefix_counts[prefix - k]
        prefix_counts[prefix] += 1

    return answer
```

Complexity: Time O(n), Space O(n)

### A5. Longest Consecutive Sequence

Problem statement:
Given an unsorted array of integers, return the length of the longest consecutive elements sequence.

Pattern recognition:
Only start counting from numbers that have no predecessor.

```python
def longest_consecutive(nums):
    values = set(nums)
    best = 0

    for x in values:
        if x - 1 in values:
            continue

        length = 1
        cur = x
        while cur + 1 in values:
            cur += 1
            length += 1

        best = max(best, length)

    return best
```

Complexity: Time O(n), Space O(n)

## B. Sliding Window / Two Pointers

Trigger: contiguous substring/subarray, longest/shortest window, sorted pair search.

### B1. Longest Substring Without Repeating Characters

Problem statement:
Given a string `s`, return the length of the longest substring without repeating characters.

Pattern recognition:
Expand right; if duplicate appears, move left past the last occurrence.

```python
def length_of_longest_substring(s):
    last_seen = {}
    left = 0
    best = 0

    for right, ch in enumerate(s):
        if ch in last_seen and last_seen[ch] >= left:
            left = last_seen[ch] + 1

        last_seen[ch] = right
        best = max(best, right - left + 1)

    return best
```

Complexity: Time O(n), Space O(min(n, charset))

### B2. Minimum Window Substring

Problem statement:
Given strings `s` and `t`, return the minimum window in `s` that contains all characters of `t`.

Pattern recognition:
Track needed counts. Expand until valid, then shrink to minimal.

```python
from collections import Counter, defaultdict


def min_window(s, t):
    if not s or not t:
        return ""

    need = Counter(t)
    window = defaultdict(int)
    required = len(need)
    formed = 0
    left = 0
    best_len = float("inf")
    best_start = 0

    for right, ch in enumerate(s):
        window[ch] += 1
        if ch in need and window[ch] == need[ch]:
            formed += 1

        while formed == required:
            if right - left + 1 < best_len:
                best_len = right - left + 1
                best_start = left

            left_ch = s[left]
            window[left_ch] -= 1
            if left_ch in need and window[left_ch] < need[left_ch]:
                formed -= 1
            left += 1

    if best_len == float("inf"):
        return ""
    return s[best_start:best_start + best_len]
```

Complexity: Time O(n), Space O(charset)

### B3. Container With Most Water

Problem statement:
Given heights of vertical lines, return the maximum water area formed by two lines.

Pattern recognition:
Area is limited by the shorter side, so move the shorter pointer inward.

```python
def max_area(height):
    left = 0
    right = len(height) - 1
    best = 0

    while left < right:
        width = right - left
        best = max(best, width * min(height[left], height[right]))

        if height[left] < height[right]:
            left += 1
        else:
            right -= 1

    return best
```

Complexity: Time O(n), Space O(1)

### B4. 3Sum

Problem statement:
Given an integer array, return all unique triplets `[a,b,c]` such that `a + b + c == 0`.

Pattern recognition:
Sort, fix one number, then use two pointers for the remaining pair.

```python
def three_sum(nums):
    nums.sort()
    result = []

    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue

        left = i + 1
        right = len(nums) - 1

        while left < right:
            total = nums[i] + nums[left] + nums[right]
            if total == 0:
                result.append([nums[i], nums[left], nums[right]])
                left += 1
                right -= 1
                while left < right and nums[left] == nums[left - 1]:
                    left += 1
                while left < right and nums[right] == nums[right + 1]:
                    right -= 1
            elif total < 0:
                left += 1
            else:
                right -= 1

    return result
```

Complexity: Time O(n^2), Space O(1) excluding output.

### B5. Valid Palindrome II

Problem statement:
Given a string, return true if it can be a palindrome after deleting at most one character.

Pattern recognition:
Use two pointers. On first mismatch, try skipping either side.

```python
def valid_palindrome(s):
    def is_pal(left, right):
        while left < right:
            if s[left] != s[right]:
                return False
            left += 1
            right -= 1
        return True

    left = 0
    right = len(s) - 1

    while left < right:
        if s[left] != s[right]:
            return is_pal(left + 1, right) or is_pal(left, right - 1)
        left += 1
        right -= 1

    return True
```

Complexity: Time O(n), Space O(1)

## C. Strings / Stack / Parsing / Simulation

Trigger: remove/cancel tokens, validate syntax, parse expression, preserve order while processing.

### C1. Remove All Occurrences of a Substring

Problem statement:
Given strings `s` and `part`, repeatedly remove the leftmost occurrence of `part` from `s` until no occurrence remains.

Pattern recognition:
Build output as a stack; whenever the stack suffix equals `part`, pop it.

```python
def remove_occurrences(s, part):
    stack = []
    m = len(part)

    for ch in s:
        stack.append(ch)
        if len(stack) >= m and "".join(stack[-m:]) == part:
            for _ in range(m):
                stack.pop()

    return "".join(stack)
```

Complexity: Time O(n*m), Space O(n)

### C2. Basic Calculator II

Problem statement:
Given a string expression containing non-negative integers and `+`, `-`, `*`, `/`, evaluate it. Division truncates toward zero.

Pattern recognition:
Push numbers for `+` and `-`; apply `*` and `/` immediately to the previous stack value.

```python
def calculate(s):
    stack = []
    num = 0
    op = "+"

    for i, ch in enumerate(s):
        if ch.isdigit():
            num = num * 10 + int(ch)

        if (not ch.isdigit() and ch != " ") or i == len(s) - 1:
            if op == "+":
                stack.append(num)
            elif op == "-":
                stack.append(-num)
            elif op == "*":
                stack.append(stack.pop() * num)
            elif op == "/":
                prev = stack.pop()
                stack.append(int(prev / num))

            op = ch
            num = 0

    return sum(stack)
```

Complexity: Time O(n), Space O(n)

### C3. Valid Parentheses

Problem statement:
Given a string containing `()[]{}`, return true if the brackets are valid and properly nested.

Pattern recognition:
Every closing bracket must match the most recent unmatched opening bracket.

```python
def is_valid_parentheses(s):
    pairs = {")": "(", "]": "[", "}": "{"}
    stack = []

    for ch in s:
        if ch in pairs.values():
            stack.append(ch)
        elif ch in pairs:
            if not stack or stack.pop() != pairs[ch]:
                return False

    return not stack
```

Complexity: Time O(n), Space O(n)

### C4. String Compression

Problem statement:
Given an array of characters, compress it in-place by replacing runs with char plus count. Return the new length.

Pattern recognition:
Use a read pointer to count runs and a write pointer to overwrite the array.

```python
def compress(chars):
    write = 0
    read = 0

    while read < len(chars):
        ch = chars[read]
        count = 0

        while read < len(chars) and chars[read] == ch:
            read += 1
            count += 1

        chars[write] = ch
        write += 1

        if count > 1:
            for digit in str(count):
                chars[write] = digit
                write += 1

    return write
```

Complexity: Time O(n), Space O(1)

### C5. Rotate String

Problem statement:
Given strings `s` and `goal`, return true if `s` can become `goal` after some number of left shifts.

Pattern recognition:
Every rotation of `s` is a substring of `s + s`.

```python
def rotate_string(s, goal):
    return len(s) == len(goal) and goal in (s + s)
```

Complexity: Time O(n) average depending on substring implementation, Space O(n)

## D. Greedy / Arrays / Intervals

Trigger: minimum steps/resources, farthest reach, intervals, local best choice.

### D1. Jump Game II

Problem statement:
Given an array where each element is the maximum jump length from that position, return the minimum number of jumps to reach the last index.

Pattern recognition:
Within the current jump range, track the farthest next reach. When you hit the end of the range, take a jump.

```python
def jump(nums):
    if len(nums) <= 1:
        return 0

    jumps = 0
    current_end = 0
    farthest = 0

    for i in range(len(nums) - 1):
        farthest = max(farthest, i + nums[i])

        if i == current_end:
            jumps += 1
            current_end = farthest

    return jumps
```

Complexity: Time O(n), Space O(1)

### D2. Best Time to Buy and Sell Stock II

Problem statement:
Given daily prices, return the maximum profit with as many buy/sell transactions as you want, but you can hold only one stock at a time.

Pattern recognition:
Every upward move is profit. Sum positive differences.

```python
def max_profit(prices):
    profit = 0

    for i in range(1, len(prices)):
        if prices[i] > prices[i - 1]:
            profit += prices[i] - prices[i - 1]

    return profit
```

Complexity: Time O(n), Space O(1)

### D3. Merge Intervals

Problem statement:
Given intervals `[start, end]`, merge all overlapping intervals.

Pattern recognition:
Sort by start. If next starts before current ends, merge.

```python
def merge(intervals):
    if not intervals:
        return []

    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0]]

    for start, end in intervals[1:]:
        last = merged[-1]
        if start <= last[1]:
            last[1] = max(last[1], end)
        else:
            merged.append([start, end])

    return merged
```

Complexity: Time O(n log n), Space O(n)

### D4. Meeting Rooms II

Problem statement:
Given meeting time intervals, return the minimum number of rooms required.

Pattern recognition:
Sort by start time. Use a min-heap of active meeting end times.

```python
import heapq


def min_meeting_rooms(intervals):
    if not intervals:
        return 0

    intervals.sort(key=lambda x: x[0])
    active_ends = []

    for start, end in intervals:
        if active_ends and active_ends[0] <= start:
            heapq.heappop(active_ends)
        heapq.heappush(active_ends, end)

    return len(active_ends)
```

Complexity: Time O(n log n), Space O(n)

### D5. Product of Array Except Self

Problem statement:
Given an integer array, return an array where each output index is the product of all input elements except itself. Do not use division.

Pattern recognition:
Build prefix products and multiply by suffix products in a second pass.

```python
def product_except_self(nums):
    result = [1] * len(nums)

    prefix = 1
    for i in range(len(nums)):
        result[i] = prefix
        prefix *= nums[i]

    suffix = 1
    for i in range(len(nums) - 1, -1, -1):
        result[i] *= suffix
        suffix *= nums[i]

    return result
```

Complexity: Time O(n), Space O(1) excluding output.

## E. Trees: BFS / DFS

Trigger: tree levels, paths, ancestors, subtree return values.

### E1. Binary Tree Right Side View

Problem statement:
Given a binary tree, return the values visible when viewing it from the right side.

Pattern recognition:
Level-order traversal; take the last node from each level.

```python
from collections import deque


def right_side_view(root):
    if not root:
        return []

    result = []
    queue = deque([root])

    while queue:
        level_size = len(queue)
        for i in range(level_size):
            node = queue.popleft()
            if i == level_size - 1:
                result.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)

    return result
```

Complexity: Time O(n), Space O(width)

### E2. Maximum Depth of Binary Tree

Problem statement:
Given a binary tree, return its maximum depth.

Pattern recognition:
Each node returns `1 + max(left depth, right depth)`.

```python
def max_depth(root):
    if not root:
        return 0

    return 1 + max(max_depth(root.left), max_depth(root.right))
```

Complexity: Time O(n), Space O(h)

### E3. Lowest Common Ancestor of a Binary Tree

Problem statement:
Given a binary tree and two nodes `p` and `q`, return their lowest common ancestor.

Pattern recognition:
If p and q split across left and right, current root is the answer.

```python
def lowest_common_ancestor(root, p, q):
    if not root or root == p or root == q:
        return root

    left = lowest_common_ancestor(root.left, p, q)
    right = lowest_common_ancestor(root.right, p, q)

    if left and right:
        return root
    return left or right
```

Complexity: Time O(n), Space O(h)

### E4. Path Sum II

Problem statement:
Given a binary tree and a target sum, return all root-to-leaf paths where the path sum equals the target.

Pattern recognition:
DFS backtracking: choose node, recurse, unchoose node.

```python
def path_sum(root, target_sum):
    result = []
    path = []

    def dfs(node, remaining):
        if not node:
            return

        path.append(node.val)
        remaining -= node.val

        if not node.left and not node.right and remaining == 0:
            result.append(path[:])
        else:
            dfs(node.left, remaining)
            dfs(node.right, remaining)

        path.pop()

    dfs(root, target_sum)
    return result
```

Complexity: Time O(n*h) output-sensitive, Space O(h)

### E5. Serialize and Deserialize Binary Tree

Problem statement:
Design methods to serialize a binary tree into a string and deserialize the string back into the original tree.

Pattern recognition:
Preorder traversal with null markers uniquely captures structure.

```python
class Codec:
    def serialize(self, root):
        values = []

        def dfs(node):
            if not node:
                values.append("#")
                return
            values.append(str(node.val))
            dfs(node.left)
            dfs(node.right)

        dfs(root)
        return ",".join(values)

    def deserialize(self, data):
        values = iter(data.split(","))

        def dfs():
            value = next(values)
            if value == "#":
                return None
            node = TreeNode(int(value))
            node.left = dfs()
            node.right = dfs()
            return node

        return dfs()
```

Complexity: Time O(n), Space O(n)

## F. Graphs: BFS / DFS / Topological Sort

Trigger: connected components, grids, dependencies, shortest spread, clone/copy graph.

### F1. Number of Islands

Problem statement:
Given a grid of `"1"` land and `"0"` water, count the number of islands. An island is connected horizontally or vertically.

Pattern recognition:
Each unvisited land cell starts one connected component.

```python
def num_islands(grid):
    if not grid:
        return 0

    rows = len(grid)
    cols = len(grid[0])
    islands = 0

    def dfs(r, c):
        if r < 0 or c < 0 or r == rows or c == cols:
            return
        if grid[r][c] != "1":
            return

        grid[r][c] = "0"
        dfs(r + 1, c)
        dfs(r - 1, c)
        dfs(r, c + 1)
        dfs(r, c - 1)

    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == "1":
                islands += 1
                dfs(r, c)

    return islands
```

Complexity: Time O(m*n), Space O(m*n) worst-case recursion.

### F2. Clone Graph

Problem statement:
Given a reference to a node in a connected undirected graph, return a deep copy of the graph.

Pattern recognition:
Use a map from original node to copied node to avoid cycles and duplicate copies.

```python
def clone_graph(node):
    if not node:
        return None

    copies = {}

    def dfs(cur):
        if cur in copies:
            return copies[cur]

        copy = Node(cur.val)
        copies[cur] = copy

        for nei in cur.neighbors:
            copy.neighbors.append(dfs(nei))

        return copy

    return dfs(node)
```

Complexity: Time O(V+E), Space O(V)

### F3. Course Schedule

Problem statement:
Given `numCourses` and prerequisite pairs `[course, prereq]`, return true if you can finish all courses.

Pattern recognition:
Dependency graph. Use indegree and process zero-prerequisite courses.

```python
from collections import defaultdict, deque


def can_finish(num_courses, prerequisites):
    graph = defaultdict(list)
    indegree = [0] * num_courses

    for course, prereq in prerequisites:
        graph[prereq].append(course)
        indegree[course] += 1

    queue = deque()
    for course in range(num_courses):
        if indegree[course] == 0:
            queue.append(course)

    completed = 0
    while queue:
        course = queue.popleft()
        completed += 1

        for nxt in graph[course]:
            indegree[nxt] -= 1
            if indegree[nxt] == 0:
                queue.append(nxt)

    return completed == num_courses
```

Complexity: Time O(V+E), Space O(V+E)

### F4. Rotting Oranges

Problem statement:
Given a grid with fresh oranges, rotten oranges, and empty cells, return minutes until all fresh oranges rot, or -1 if impossible.

Pattern recognition:
Multi-source BFS from all initially rotten oranges.

```python
from collections import deque


def oranges_rotting(grid):
    rows = len(grid)
    cols = len(grid[0])
    queue = deque()
    fresh = 0

    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == 2:
                queue.append((r, c, 0))
            elif grid[r][c] == 1:
                fresh += 1

    minutes = 0
    directions = [(1, 0), (-1, 0), (0, 1), (0, -1)]

    while queue:
        r, c, minutes = queue.popleft()

        for dr, dc in directions:
            nr = r + dr
            nc = c + dc
            if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 1:
                grid[nr][nc] = 2
                fresh -= 1
                queue.append((nr, nc, minutes + 1))

    return minutes if fresh == 0 else -1
```

Complexity: Time O(m*n), Space O(m*n)

### F5. Pacific Atlantic Water Flow

Problem statement:
Given heights, return coordinates where water can flow to both the Pacific and Atlantic oceans. Water flows from high/equal to low/equal neighbors.

Pattern recognition:
Reverse the flow: start BFS/DFS from ocean borders and move uphill.

```python
def pacific_atlantic(heights):
    rows = len(heights)
    cols = len(heights[0])

    def dfs(r, c, visited, prev_height):
        if r < 0 or c < 0 or r == rows or c == cols:
            return
        if (r, c) in visited or heights[r][c] < prev_height:
            return

        visited.add((r, c))
        height = heights[r][c]
        dfs(r + 1, c, visited, height)
        dfs(r - 1, c, visited, height)
        dfs(r, c + 1, visited, height)
        dfs(r, c - 1, visited, height)

    pacific = set()
    atlantic = set()

    for c in range(cols):
        dfs(0, c, pacific, heights[0][c])
        dfs(rows - 1, c, atlantic, heights[rows - 1][c])

    for r in range(rows):
        dfs(r, 0, pacific, heights[r][0])
        dfs(r, cols - 1, atlantic, heights[r][cols - 1])

    return list(pacific & atlantic)
```

Complexity: Time O(m*n), Space O(m*n)

## G. Heap / Priority Queue

Trigger: top k, closest k, merge sorted streams, active intervals, next min/max repeatedly.

### G1. Top K Frequent Elements

Problem statement:
Given an array of integers and `k`, return the `k` most frequent elements.

Pattern recognition:
Use a min-heap of size k to keep only the best k counts.

```python
from collections import Counter
import heapq


def top_k_frequent_heap(nums, k):
    counts = Counter(nums)
    heap = []

    for num, count in counts.items():
        heapq.heappush(heap, (count, num))
        if len(heap) > k:
            heapq.heappop(heap)

    return [num for count, num in heap]
```

Complexity: Time O(n log k), Space O(n)

### G2. K Closest Points to Origin

Problem statement:
Given points `[x, y]`, return the k points closest to the origin.

Pattern recognition:
Closest means smallest squared distance. Keep a max-heap of size k using negative distances.

```python
import heapq


def k_closest(points, k):
    heap = []

    for x, y in points:
        dist = x * x + y * y
        heapq.heappush(heap, (-dist, x, y))
        if len(heap) > k:
            heapq.heappop(heap)

    return [[x, y] for dist, x, y in heap]
```

Complexity: Time O(n log k), Space O(k)

### G3. Meeting Rooms II

Problem statement:
Given meeting intervals, return the minimum rooms needed.

Pattern recognition:
Heap stores meetings currently using rooms by earliest end time.

```python
import heapq


def min_meeting_rooms_heap(intervals):
    intervals.sort(key=lambda x: x[0])
    heap = []

    for start, end in intervals:
        if heap and heap[0] <= start:
            heapq.heappop(heap)
        heapq.heappush(heap, end)

    return len(heap)
```

Complexity: Time O(n log n), Space O(n)

### G4. Task Scheduler

Problem statement:
Given tasks represented by letters and cooldown `n`, return the least number of intervals needed to finish all tasks.

Pattern recognition:
The most frequent task creates idle slots. Use formula based on max frequency.

```python
from collections import Counter


def least_interval(tasks, n):
    counts = Counter(tasks)
    max_freq = max(counts.values())
    num_max = sum(1 for count in counts.values() if count == max_freq)

    frame = (max_freq - 1) * (n + 1) + num_max
    return max(len(tasks), frame)
```

Complexity: Time O(n), Space O(1) because at most 26 task types.

### G5. Merge K Sorted Lists

Problem statement:
Given k sorted linked lists, merge them into one sorted linked list.

Pattern recognition:
Always take the current smallest head among k lists.

```python
import heapq


def merge_k_lists(lists):
    heap = []

    for i, node in enumerate(lists):
        if node:
            heapq.heappush(heap, (node.val, i, node))

    dummy = ListNode(0)
    tail = dummy

    while heap:
        value, i, node = heapq.heappop(heap)
        tail.next = node
        tail = tail.next

        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))

    return dummy.next
```

Complexity: Time O(N log k), Space O(k)

## H. Design / Data Structures

Trigger: implement API, O(1) operations, combine lookup with order/min/max/history.

### H1. LRU Cache

Problem statement:
Design an LRU cache with `get(key)` and `put(key, value)` in O(1). When capacity is exceeded, evict the least recently used key.

Pattern recognition:
Hashmap gives O(1) lookup. Doubly linked list gives O(1) recency updates.

```python
class Node:
    def __init__(self, key=0, value=0):
        self.key = key
        self.value = value
        self.prev = None
        self.next = None


class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.cache = {}

        self.left = Node()
        self.right = Node()
        self.left.next = self.right
        self.right.prev = self.left

    def _remove(self, node):
        prev_node = node.prev
        next_node = node.next
        prev_node.next = next_node
        next_node.prev = prev_node

    def _insert_recent(self, node):
        prev_node = self.right.prev
        prev_node.next = node
        node.prev = prev_node
        node.next = self.right
        self.right.prev = node

    def get(self, key):
        if key not in self.cache:
            return -1

        node = self.cache[key]
        self._remove(node)
        self._insert_recent(node)
        return node.value

    def put(self, key, value):
        if key in self.cache:
            self._remove(self.cache[key])

        node = Node(key, value)
        self.cache[key] = node
        self._insert_recent(node)

        if len(self.cache) > self.capacity:
            lru = self.left.next
            self._remove(lru)
            del self.cache[lru.key]
```

Complexity: Time O(1) per operation, Space O(capacity)

### H2. Min Stack

Problem statement:
Design a stack that supports push, pop, top, and retrieving the minimum element in O(1).

Pattern recognition:
Store the current minimum alongside each pushed value.

```python
class MinStack:
    def __init__(self):
        self.stack = []

    def push(self, val):
        current_min = val if not self.stack else min(val, self.stack[-1][1])
        self.stack.append((val, current_min))

    def pop(self):
        self.stack.pop()

    def top(self):
        return self.stack[-1][0]

    def getMin(self):
        return self.stack[-1][1]
```

Complexity: Time O(1) per operation, Space O(n)

### H3. Design HashMap

Problem statement:
Design a hash map without using built-in hash map libraries. Support put, get, and remove.

Pattern recognition:
Use buckets. Each bucket stores key-value pairs for collisions.

```python
class MyHashMap:
    def __init__(self):
        self.size = 1009
        self.buckets = [[] for _ in range(self.size)]

    def _bucket(self, key):
        return self.buckets[key % self.size]

    def put(self, key, value):
        bucket = self._bucket(key)
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return
        bucket.append((key, value))

    def get(self, key):
        bucket = self._bucket(key)
        for k, v in bucket:
            if k == key:
                return v
        return -1

    def remove(self, key):
        bucket = self._bucket(key)
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket.pop(i)
                return
```

Complexity: Time O(1) average, O(n) worst, Space O(n)

### H4. Time Based Key-Value Store

Problem statement:
Design a key-value store that supports `set(key, value, timestamp)` and `get(key, timestamp)`, where get returns the value with the largest timestamp <= requested timestamp.

Pattern recognition:
For each key, values are timestamp sorted. Use binary search.

```python
from collections import defaultdict


class TimeMap:
    def __init__(self):
        self.store = defaultdict(list)

    def set(self, key, value, timestamp):
        self.store[key].append((timestamp, value))

    def get(self, key, timestamp):
        values = self.store[key]
        left = 0
        right = len(values) - 1
        answer = ""

        while left <= right:
            mid = (left + right) // 2
            ts, val = values[mid]
            if ts <= timestamp:
                answer = val
                left = mid + 1
            else:
                right = mid - 1

        return answer
```

Complexity: Set O(1), Get O(log n), Space O(n)

### H5. Hit Counter

Problem statement:
Design a hit counter that records hits and returns the number of hits in the past 5 minutes.

Pattern recognition:
Queue timestamps. Remove anything older than 300 seconds.

```python
from collections import deque


class HitCounter:
    def __init__(self):
        self.hits = deque()

    def hit(self, timestamp):
        self.hits.append(timestamp)

    def getHits(self, timestamp):
        while self.hits and self.hits[0] <= timestamp - 300:
            self.hits.popleft()
        return len(self.hits)
```

Complexity: Amortized Time O(1) per operation, Space O(n)

## I. Dynamic Programming

Trigger: count/min/max choices, overlapping subproblems, delete/choose/skip, amount/range state.

### I1. Valid Palindrome III

Problem statement:
Given a string `s` and integer `k`, return true if `s` can become a palindrome after removing at most `k` characters.

Pattern recognition:
Minimum deletions to make palindrome = `n - longest_palindromic_subsequence`.

```python
def is_valid_palindrome_k(s, k):
    n = len(s)
    dp = [[0] * n for _ in range(n)]

    for i in range(n - 1, -1, -1):
        dp[i][i] = 1
        for j in range(i + 1, n):
            if s[i] == s[j]:
                dp[i][j] = 2 + dp[i + 1][j - 1]
            else:
                dp[i][j] = max(dp[i + 1][j], dp[i][j - 1])

    min_deletions = n - dp[0][n - 1]
    return min_deletions <= k
```

Complexity: Time O(n^2), Space O(n^2)

### I2. Longest Palindromic Subsequence

Problem statement:
Given a string, return the length of the longest palindromic subsequence.

Pattern recognition:
Range DP. If ends match, take both; otherwise skip one end.

```python
def longest_palindrome_subseq(s):
    n = len(s)
    dp = [[0] * n for _ in range(n)]

    for i in range(n - 1, -1, -1):
        dp[i][i] = 1
        for j in range(i + 1, n):
            if s[i] == s[j]:
                dp[i][j] = 2 + dp[i + 1][j - 1]
            else:
                dp[i][j] = max(dp[i + 1][j], dp[i][j - 1])

    return dp[0][n - 1]
```

Complexity: Time O(n^2), Space O(n^2)

### I3. Coin Change

Problem statement:
Given coins and an amount, return the fewest number of coins needed to make the amount, or -1 if impossible.

Pattern recognition:
`dp[a]` is the best answer for amount `a`.

```python
def coin_change(coins, amount):
    INF = amount + 1
    dp = [INF] * (amount + 1)
    dp[0] = 0

    for a in range(1, amount + 1):
        for coin in coins:
            if a - coin >= 0:
                dp[a] = min(dp[a], dp[a - coin] + 1)

    return dp[amount] if dp[amount] != INF else -1
```

Complexity: Time O(amount * number_of_coins), Space O(amount)

### I4. House Robber

Problem statement:
Given money in houses along a street, return the maximum amount you can rob without robbing adjacent houses.

Pattern recognition:
At each house, choose rob current plus best two back, or skip current.

```python
def rob(nums):
    prev2 = 0
    prev1 = 0

    for money in nums:
        current = max(prev1, prev2 + money)
        prev2 = prev1
        prev1 = current

    return prev1
```

Complexity: Time O(n), Space O(1)

### I5. Longest Increasing Subsequence

Problem statement:
Given an integer array, return the length of the longest strictly increasing subsequence.

Pattern recognition:
Maintain the smallest possible tail for each subsequence length.

```python
import bisect


def length_of_lis(nums):
    tails = []

    for x in nums:
        i = bisect.bisect_left(tails, x)
        if i == len(tails):
            tails.append(x)
        else:
            tails[i] = x

    return len(tails)
```

Complexity: Time O(n log n), Space O(n)

## Last-Minute Recall

- Hashmap: store what avoids repeated scanning.
- Sliding window: contiguous and dynamic boundary.
- Stack: earlier item waits for a later closer/canceller.
- Greedy: local choice extends reach, profit, or earliest finish.
- Tree BFS: level by level.
- Tree DFS: subtree/path answer.
- Graph BFS/DFS: visited connected state.
- Topological sort: prerequisites and indegree.
- Heap: repeatedly need next min/max/top k.
- Design: combine hashmap with list/heap/stack/queue.
- DP: best answer for prefix, range, or amount.
