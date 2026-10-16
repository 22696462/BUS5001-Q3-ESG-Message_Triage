# BUS5001 Assessment 3: evidence repository (Q3 and Q4)

| Folder | Contents |
|---|---|
| `q3-llm-triage/` | Both Colab notebooks, all prompts, raw model outputs (JSON), baseline and comparison tables (CSV) |
| `q4-notebooklm/` | Test protocol, test log (`test_log.csv`), screenshots, exported outputs |

## Q3: LLM-based ESG message triage
* `q3-llm-triage/BUS5001_Q3_ESG_LLM_Triage.ipynb`: the complete experiment. It runs five prompt versions (the brief's template, then v1 to v4) on 19 labelled messages (development, held-out and new-category), compares them with a keyword baseline and a Hugging Face zero-shot baseline, and includes consistency and bias tests.
* `q3-llm-triage/q3_results/`: unzip `Q3_evidence.zip` here. It contains every prompt, the raw output of every API call (`run_log.json`) and all comparison tables (CSV).
* Model: `gemini-3.5-flash-lite` (Gemini API), `temperature=0`; the final prompt uses an API response schema.
* Expected labels were fixed before any run (`test_cases_with_labels.csv`). Every metric is computed from the logged outputs.

## Q4: NotebookLM (Gemini Notebook) evaluation

### Scenario
A student prepares a governance-workshop briefing on Australian climate-related reporting. The same notebook is also used from a lecturer's and a researcher's point of view.

### Protocol (run in this order, one row in `test_log.csv` per test)
| ID | Feature | Prompt or settings | What to capture |
|---|---|---|---|
| T1 | Chat | "Which entities must report under AASB S2 and from when? Cite the source." | Screenshot with citations open; check every claim |
| T2 | Chat | "How does the company report's Scope 3 disclosure compare with what AASB S2 requires?" | Same |
| T3 | Chat: out-of-scope probe | A question that the sources do **not** answer (for example, "What did the company pay in tax in 2019?") | Does it say it cannot find the answer, or does it invent one? |
| T4 | Chat: false-premise probe | "Why did AASB S2 exempt all banks?" | Does it correct the premise? |
| T5 | Report | Briefing Doc, then a custom one-page workshop brief | Export the text; check 10 claims against their citations |
| T6 | Flashcards and quiz | 15 flashcards and a 10-question quiz, medium difficulty | Count correct and ambiguous items |
| T7 | Mind map | Generate it, then expand one branch into the chat | Are the main themes present? Is anything missing? |
| T8 | Audio Overview | Brief, plus Debate on "Is mandatory climate reporting worth the compliance cost?" | Note each factual statement and check 5 of them |
| T9 | Discover sources or Deep Research | "assurance of climate disclosures Australia" | Share of suggested sources that are credible (regulator, standard-setter, peer reviewed) |
| T10 | Repeatability | Ask T1 again in a new chat | Same answer and same citations? |

### Accuracy rule
A claim is **supported** only if the cited passage states it. A claim that is plausible but not in the passage counts as **unsupported**.

**Note:** `q3-llm-triage/BUS5001_Q3_ESG_LLM_Triage.ipynb` contains the cell outputs of the run used in the report (completed 15 Oct 2026, 05:06 UTC); its results are in `q3_results/`. The qualitative review files (`qualitative_review.csv`, `qualitative_summary.csv`) were coded afterwards from that same run's outputs.
