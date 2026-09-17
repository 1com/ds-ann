# Learning Progress

This file tracks where we are in walking through this repo, block by block (see
[CLAUDE.md](CLAUDE.md) for the explanation style). At the start of any session,
read this file first to resume from the right spot instead of starting over.
Update the "Currently here" section and the relevant row every time a code
block/cell is finished being explained.

## Currently here

- **File:** day_1/02_classification_tensorflow_keras.ipynb
- **Cell / block:** cell-8/9 (VIN cleaning + median GVWR fill)
- **Notes (this notebook so far):** Cell-0/1 (intro: vehicle emissions dataset from city of Albuquerque, predicting pass/fail on emissions test — classification not regression; imports incl. new-here `termcolor`, sklearn's `train_test_split`/`confusion_matrix`/`recall_score` (classification-specific metrics, contrasted with regression's MAE/MSE), explicit `np.random.seed(42)`/`tf.random.set_seed(42)` for reproducibility (notebook 1 didn't do this); `df = pd.read_csv("../data/vehicle_emissions.csv")`; benign CUDA/oneDNN startup warning again). Cell-2/3 (variable description table + df.head() — flagged RESULT's inverted-sounding key: 0=Yes/passed, 1=No/failed, so "1" is the failure/positive class relevant to the notebook's pollution-reduction goal; VIN/MAKE need categorical handling like notebook 1's Origin; noted class balance not yet checked from just 5 head() rows). Cell-4/5 (data cleaning intro — noted this notebook skips showing df.isna()/df.info() diagnostics unlike notebook 1, so cleaning steps are taken more on faith; TEST_SDATE → pd.to_datetime, explained why .dt accessor needs real datetime not plain text, sets up VEHICLE_AGE next). Cell-6/7 (VEHICLE_AGE = test_year - model_year + 2; needed a follow-up pass on why +2 not +1 — explained US model-year-vs-calendar-year mismatch, model year cars can go on sale in fall of prior calendar year giving test_year-model_year=-1, so +1 alone insufficient, +2 guarantees always positive; noted markdown itself doesn't spell out the "why 2" reasoning explicitly, flagged as inference not certainty). MILE_YEAR (cell-17, later) = ODOMETER/VEHICLE_AGE, motivating the divide-by-zero avoidance.
- **Notes (notebook 1, DONE):** `day_1/01_regression_tensorflow_keras.ipynb` is **DONE** in full (cell-3 through cell-137, the whole notebook). Summary of what it covered and key things to carry forward:
  - Auto MPG dataset exploration/cleaning, sklearn `LinearRegression` baseline (2.39 MAE / 10.17 MSE), and a full-dataset `Normalization` layer (`normalizer`, adapted in cell-44/47).
  - **Linear regression section:** single-feature `horsepower_model` (3.64 MAE) and multi-feature `linear_model` (2.51 MAE, close to sklearn) — same normalize→Dense(1) recipe, built/compiled/trained/evaluated/plotted for both.
  - **DNN regression section:** `build_and_compile_model()` helper (normalizer→Dense(64,gelu)→Dense(64,gelu)→Dense(1), lr=0.001) used for both `dnn_horsepower_model` (3.33 MAE) and the full `dnn_model` (1.73 MAE — best of all 5, beats sklearn).
  - **Two things flagged and worth remembering:** (1) cell-108 has a genuine bug — it evaluates `dnn_horsepower_model` on `X_train`/`y_train` instead of `X_test`/`y_test` like every other model, so that row in the final comparison table isn't a fair comparison; user chose to leave this unfixed. (2) The Conclusion (cell-129) claims "overfitting wasn't a problem for this tutorial," but `dnn_model`'s own loss curve (cell-113) showed a real, mild train/val gap — a discrepancy worth noting, and it foreshadows `day_2/03_overfit_underfit.ipynb`.
  - Also covered: predictions-vs-actual scatter + error histogram for `dnn_model`, saving/reloading the model (`dnn_model.save("dnn_model.keras")` — this is the untracked file seen in git status, a regenerable artifact not worth committing), and a TensorBoard section connecting `get_callbacks()`/`get_run_logdir()` (cell-8/10) to every `.fit()` call made throughout the notebook.
  - IMPORTANT standing instructions for this walkthrough style: always explain/interpret block OUTPUT, not just code (CLAUDE.md + memory); AskUserQuestion "Next" needs a genuine 2nd option since the tool rejects single-option questions — use "I have a question first"; this user benefits from plain-language, concrete/example-driven explanations and sometimes needs 2+ passes on a dense cell (e.g. KerasTensor/shape concepts, Python trailing-comma syntax) — avoid stacking jargon in one go.

## Suggested order & status

| # | File | Status | Notes |
|---|------|--------|-------|
| 1 | day_1/01_regression_tensorflow_keras.ipynb | done | full notebook walked cell-3 to cell-137 |
| 2 | day_1/02_classification_tensorflow_keras.ipynb | in progress | started at cell-0 |
| 3 | day_2/03_overfit_underfit.ipynb | not started | notebook 1 flagged a real (mild) overfitting example worth revisiting here |
| 4 | day_2/04_load_saved_models.ipynb | not started | |
| 5 | day_3/cnn/cnn_keras.ipynb | not started | |
| 6 | day_3/pretrained_transfer_learning/pretrained_networks-transfer_learning.ipynb | not started | |
| 7 | bonus/00_dnn_from_scratch.ipynb | not started | optional deep dive |

Status values: `not started`, `in progress`, `done`.

## Log

_(Running log of sessions — one line per session, most recent first.)_

- 2026-09-16: Finished the rest of `day_1/01_regression_tensorflow_keras.ipynb` (cell-55 through cell-137) — single/multi-feature linear and DNN regression models, final comparison table, save/reload, TensorBoard section. Notebook 1 is now fully done. Flagged a real bug (cell-108 test/train mix-up, left unfixed by user's choice) and a real discrepancy (Conclusion's overfitting claim vs. the actual loss curve). Resume next session with `day_1/02_classification_tensorflow_keras.ipynb`.
- 2026-09-16 (earlier): Finished "One Variable" linear regression section (cell-55–76) in day_1/01_regression_tensorflow_keras.ipynb — built, trained, evaluated, and plotted `horsepower_model`. Resumed at cell-79 ("Multiple inputs").
