# RULES: India AQI Analysis and Prediction

Instructions for the coding agent working in this project. Read PRD.md, ARCHITECTURE.md and TASKS.md before starting, and follow TASKS.md in order.

## General
- Follow the phases in TASKS.md. Do not skip ahead, and do not add features outside PRD.md scope.
- If a requirement is unclear, ask rather than guess.
- Keep the project simple and readable. This is a student internship submission, so clarity beats cleverness.

## Deliverables (must match exactly)
- `AshishSingh_IndiaAQI_Prediction.ipynb`
- `requirements.txt`
- `AshishSingh_ProjectReport.docx`
- `README.md`

## Notebook Conventions
- Every section starts with a markdown heading and a 1-2 line explanation of what and why.
- Every chart has a title, labeled axes, and a markdown takeaway below it.
- One clear purpose per code cell. No dead or commented-out experiment code in the final version.
- Set `random_state=42` everywhere randomness appears.
- The notebook must pass "Restart and Run All" with no errors.
- Read data from `data/city_day.csv` using a relative path.

## Data and Modeling Rules
- Never split time-series data randomly. Use a chronological split.
- Compute lag and rolling features **within each city** (`groupby('City')`).
- Fit imputers, scalers and encoders on training data only, then apply them to test data.
- Do not use future information to fill or predict the past.
- Always compare against the persistence baseline.
- Report MAE, RMSE and R2 for every model in one comparison table.
- Do not claim results the notebook does not show. All numbers in the report and README must come from executed cells.

## Code Style
- PEP 8, snake_case names, short docstrings for any helper function.
- Put imports in the first code cell only.
- No hard-coded absolute paths.
- Do not commit the dataset. Keep `data/` in `.gitignore`.

## Dependencies
- Only add a library to `requirements.txt` if the notebook imports it.
- Test `requirements.txt` in a fresh virtual environment before finalizing.

## Documentation
- README must include: overview, dataset link, project description, technologies used, setup and run instructions, key results.
- The report must use figures and numbers taken from the notebook, and be consistent with it.

## Do Not
- Do not fabricate data, metrics or citations.
- Do not rename deliverable files.
- Do not add web apps, APIs or deployment unless explicitly requested.
