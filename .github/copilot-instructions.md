# Repository Guidelines

## Project shape

This repository contains CS 315 teaching materials, primarily Python/Jupyter notebooks demonstrating SQL, SQLite, DuckDB, and pandas:

- `sqlite3-tutorial.ipynb` introduces Python's built-in `sqlite3` API and using pandas with SQLite.
- `week8-tue-worksheet.ipynb` loads `netflix_top10_countries.tsv` into pandas.
- `week8-tue-duckdb.ipynb` solves the same worksheet tasks with DuckDB queries against `netflix_data.db`.
- `sql vs pandas/SQL tutorial.ipynb` compares pandas operations with SQL over the student CSV files and `school_database.db`. `sql vs pandas/create_db.py` generates that SQLite database.

## Running and validation

There is no project build, test suite, or lint configuration. Open a notebook in VS Code/Jupyter, select a Python kernel with the notebook's imports available, and run its cells in order; to validate a focused notebook change, run the changed cell and any dependent cells. The SQLite tutorial uses the Python standard library; the data-analysis notebooks also use pandas, and the DuckDB notebook uses `duckdb`.

To regenerate the school database, run `python create_db.py` with the working directory set to `sql vs pandas` (or run `cd "sql vs pandas" && python create_db.py` from the repository root). The script removes and recreates `school_database.db` in the current working directory, so only run it when replacing that database is intended.

## Data and notebook conventions

- Data paths in notebook cells are relative to the notebook kernel's working directory. The Week 8 notebooks expect the repository root; the SQL-vs-pandas notebook expects `sql vs pandas` so its CSV and SQLite paths resolve.
- Keep the paired SQL and pandas examples aligned when editing the SQL-vs-pandas tutorial. The current `student_grades.csv` has rows for student IDs 17 and 18 that `create_db.py` omits because its database enforces a student foreign key; do not assume the CSV and generated database contain identical rows.
- Notebooks are instructional documents with explanatory Markdown and stateful Python cells. Preserve the narrative and run-order dependencies when editing, and verify downstream cells after changing setup or data-loading cells.
