# Data Science Technical Challenge

This repository contains my solution for the Data Science technical challenge.

The task is based on the daily bike sharing demand dataset and focuses on exploratory analysis, fleet sizing logic, demand forecasting, and business-oriented interpretation of the results.

## Repository Structure

```text
.
├── data/
│   └── raw/
│       ├── day.csv
│       └── Data_Readme.txt
├── outputs/
│   └── DataScience_Task_202605.html
├── DataScience_Task_202605.ipynb
├── requirements.txt
├── requirements-freeze.txt
├── pyproject.toml
├── uv.lock
└── README.md
```

## Files

- `DataScience_Task_202605.ipynb`  
  Main notebook containing the complete analysis, methodology, code, results, and reflection.

- `outputs/DataScience_Task_202605.html`  
  Rendered HTML version of the notebook for convenient review without executing the notebook.

- `data/raw/day.csv`  
  Input dataset used for the analysis.

- `data/raw/Data_Readme.txt`
  Readme file for the dataset.  

- `requirements.txt`  
  Python dependencies required to run the notebook.

- `requirements-freeze.txt`  
  Is included as an additional environment snapshot generated via `pip freeze`. `requirements.txt` was generated via uv. If it's not working/displayed properly, this alternative file can be used.

- `pyproject.toml` and `uv.lock`  
  Project environment files used for dependency management with `uv`.

## Environment Setup

The project was developed with Python and `uv`.

To create and install the environment from `requirements.txt`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Alternatively, using `uv`:

```bash
uv sync
```

## Running the Notebook

After installing the dependencies, start Jupyter and open the notebook:

```bash
jupyter notebook DataScience_Task_202605.ipynb
```

or with `uv`:

```bash
uv run jupyter notebook DataScience_Task_202605.ipynb
```

The notebook is designed to be executed from the repository root. The expected input path is:

```text
data/raw/day.csv
```

## Exporting the Notebook to HTML

The HTML version can be regenerated with:

```bash
uv run jupyter nbconvert --to html DataScience_Task_202605.ipynb --output-dir outputs
```

## Methodological Notes

The solution follows a time-aware evaluation setup. The final 30 days are held out as a test period and are not used for model fitting.

Key methodological choices include:

- using a chronological train/test split instead of a random split,
- excluding leakage-prone variables such as `casual`, `registered`, and derived target fields,
- using MAE as the primary evaluation metric due to its direct business interpretability,
- reporting RMSE as an additional diagnostic metric for larger forecast errors,
- keeping the model specification deliberately simple and robust for a small two-year daily dataset.

## Main Output

The analysis covers:

1. Data understanding and preprocessing
2. Fleet size estimation based on historical daily demand
3. Forecasting daily rental demand
4. Model evaluation and business interpretation
5. Reflection on limitations and potential production extensions

## Notes on Reproducibility

The notebook output has been saved before submission, and an HTML export is included to make the review process easier.