# Northstar refunds: BMAD lab starter

Northstar is a fictional online retailer. Support agents submit customer refunds, and finance should review high-value requests. The application in this repository approves any positive amount immediately. The change requested in GitHub issue 1 is to route refunds above $500 to finance approval, capture a reason, audit who did what and stop duplicate submissions.

This repository is the starting point for a lab that delivers that change with the BMAD method. It contains the baseline application and the synthetic policy documents, and nothing else.

| Path | What it is |
|---|---|
| `app.py`, `index.html` | The baseline FastAPI service and its simple page |
| `tests/test_baseline.py` | One test that records today's behaviour |
| `policy-docs/` | Synthetic business documents (DOC-1 to DOC-8). Check each document's status before relying on it |
| `CLAUDE.md` | Project instructions that Claude Code reads |

## Run the baseline

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\python -m pip install -r requirements.txt
.\.venv\Scripts\python -m pytest -q
.\.venv\Scripts\python -m uvicorn app:app --reload
```

macOS / Linux:

```bash
python3 -m venv .venv
./.venv/bin/python -m pip install -r requirements.txt
./.venv/bin/python -m pytest -q
./.venv/bin/python -m uvicorn app:app --reload
```

Open http://127.0.0.1:8000 and submit $501.00: the response is approved immediately. Use synthetic data only.
