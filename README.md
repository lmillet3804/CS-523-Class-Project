# CS-523-Class-Project

Trend analysis of spring migrants on Dauphin Island, AL from eBird data.

- `dauphin_dataset.ipynb` – filters the eBird Basic Dataset (DuckDB) to Dauphin Island and writes zero-filled parquet files.
- `analysis.ipynb` – runs the trend/effort analysis on those files.

## Setup

Requires Python 3.11+. Run these commands from the project folder:

```bash
python3 -m venv .venv                # create an isolated environment
source .venv/bin/activate            # Windows: .venv\Scripts\activate
pip install -r requirements.txt      # install the pinned package versions
cp .env.example .env                 # Windows: copy .env.example .env
jupyter lab                          # open the notebooks
```

Then edit `.env` to point at the data files on your machine.

## Configuring dataset paths

Machine-specific paths live in `.env`, which is git-ignored and loaded by both notebooks
via `python-dotenv`. `.env.example` lists every variable (e.g. `EBD_SRC_DB` for the source
DuckDB file, `DATA_DIR` for the parquet output/input, `RESULTS_DIR`). Unset variables fall
back to the defaults in the notebooks' config cells, so keep a different `.env` per machine.
Run `dauphin_dataset.ipynb` first, then `analysis.ipynb`.
