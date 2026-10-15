# Q4: NotebookLM (Gemini Notebook) evaluation, 15 October 2026

**Scenario:** a BUS5001 governance-workshop briefing on Australian mandatory climate reporting.
**Sources in the notebook:** AASB S2 Climate-related Disclosures (Sept 2024), ASIC RG 280 Sustainability Reporting (March 2025), and the Woolworths Group 2025 Sustainability Report. These are public documents; get them from aasb.gov.au, asic.gov.au and woolworthsgroup.com.au.

**Method:** 11 tests (T0–T10), run in order. Each factual claim was checked against the source passage:
**supported** = the cited passage states it; **partly** = overstated or missing a qualification; **unsupported** = not in the source.
Two trap questions (out-of-scope and false premise) and one repeatability test.

| Result | Value |
|---|---|
| Claims checked | 163 |
| Supported | 150 (92%) |
| Partly supported | 10 (6%) |
| Unsupported | 3 (2%), all in long Studio outputs; 0 in chat |

**Files:** `test_log.csv` (one row per test), `outputs/` (exported answers, flashcards, audio), `screenshots/`.
