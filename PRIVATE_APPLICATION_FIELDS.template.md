# Private Application Fields Template

Create a local `PRIVATE_APPLICATION_FIELDS.md` from this template when running agents on this machine.

Do not commit the real `PRIVATE_APPLICATION_FIELDS.md`.

## Official ATS Identity Fields

- Last four digits of SSN: `<last_four_ssn>`
- Date of birth: `<month day, year>`
- DOB numeric format: `<MM/DD/YYYY>`
- DOB ISO format: `<YYYY-MM-DD>`
- DOB month/day format for Workday-style fields: `<MMDD>`
- DOB day-month-year display format: `<DD Mon YYYY>`

## Usage Rules

- Use these values only inside official ATS/company application forms when the form requires last-4 SSN, date of birth, or month/day birth fields.
- Never write private identity values into trackers, Gmail summaries, screenshots, notes, learning-loop entries, or GitHub.
- If a form asks for full SSN, full government ID, passport number, bank details, payment, or suspicious identity collection beyond normal ATS identity verification, mark the role `Blocked - Other` and continue. Use `Blocked - CAPTCHA` only for true visual CAPTCHA/hCaptcha/reCAPTCHA/anti-abuse challenges.
