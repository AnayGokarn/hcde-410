# A3 — Watching the Machine

My submission for HCDE 410 Assignment 3. In this assignment, **AI is the subject of study, not the author.** It is a small mixed-methods study of how reliable and reproducible large language models (LLMs) are, and how people check what they produce.

## What's in this repo

| File | What it is |
|---|---|
| `A3_watching_the_machine_starter.ipynb` | The main deliverable. All five sections, with written answers and the code that loads and summarizes the data. |
| `A3_watching_the_machine_starter.html` | The same notebook exported to HTML (with outputs), so it can be read without Jupyter. |
| `a3_runs.xlsx` / `a3_runs.csv` | The reproducibility probe log: one row per run. The notebook reads the CSV. |
| `a3_codes.xlsx` / `a3_codes.csv` | Coded field notes from the observation: one row per note, with a theme. The notebook reads the CSV. |
| `LICENSE` | MIT License. |

The `.xlsx` files are where the data is entered and edited. The `.csv` files are exported from them and are what the notebook actually loads.

## The study

The notebook has five parts:

1. **Prior practice:** how I use LLMs now and what I assume about their reliability.
2. **Reproducibility probe:** I gave the same prompt (write Python code that summarizes a list of ten numbers: min, max, range, median, mode, Q1, Q3, IQR, and the sorted list) to Claude Opus 5.5 three times and to ChatGPT (GPT-6 Instant) once. I logged every output in full and checked each one against answers worked out by hand and by running the code.
3. **Observation:** field notes on two people (P1 and P2) using Claude Haiku 5.5 to summarize why AI has raised RAM prices, and to check the answer however they normally would. Each note is coded with a theme, and the themes are counted by person.
4. **Synthesis & reflection:** what the probe and the observation mean together for trustworthy, reproducible research, and what I'll change in my own work.
5. **Competency declaration & AI use.**

### Main findings

- **Same prompt, different results.** All three Claude runs gave the correct numbers, but the code, formatting, and side notes were different every time. Saving the prompt is not enough to reproduce a result.
- **The errors were around the answer, not in it.** ChatGPT's "expected output" listed a Q3 and IQR that its own code would never print. One of Claude's side notes gave a wrong value for a different Python function. Both were stated with full confidence.
- **People's checks didn't target those errors.** In the observation, people judged format first, asked the same AI whether it was right, and stopped once something agreed with it. None of those checks would have caught the errors in the probe.

## How to run

You need Python with `pandas` (plus `jupyter` to open the notebook):

```bash
pip install pandas jupyter
```

Keep `a3_runs.csv` and `a3_codes.csv` in the same folder as the notebook, then open the notebook and run all the cells:

```bash
jupyter notebook A3_watching_the_machine_starter.ipynb
```

If you change either spreadsheet, export it to CSV again (File > Save As > CSV) using the same file name before you re-run the notebook.

To rebuild the HTML version:

```bash
python -m nbconvert --to html --execute A3_watching_the_machine_starter.ipynb
```

If you get a `FileNotFoundError`, check that the CSV file names match exactly and that the files are in the same folder as the notebook.

## AI use

The full statement is in the notebook's last section. In short:

- Claude Opus 5.5, ChatGPT (GPT-6 Instant), and Claude Haiku 5.5 are the **subjects** of the study.
- Claude code was used to help draft the README.md

## License

Released under the MIT License. See [`LICENSE`](./LICENSE).