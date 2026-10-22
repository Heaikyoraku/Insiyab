# Evaluation notes — Insiyab

This note is kept separate from the main README so the project overview can focus on what was built without overstating the confidence of its metrics.

## Original experiment

- A synthetic 10,000-row metro dataset was used.
- A Keras LSTM classifier was trained to predict low / medium / high congestion.
- The original report described approximately 95% accuracy on its test split.

## Methodological observations from the notebook

1. **Preprocessing before the split:** The `MinMaxScaler` was fitted on the complete dataframe before `train_test_split`. The held-out set therefore informed preprocessing.
2. **Test split used for validation:** `model.fit(... validation_data=(X_test_lstm, y_test))` uses the same holdout for model selection/early stopping, so it is not an untouched final test.
3. **Sequence length is one:** `np.expand_dims(..., axis=1)` yields one timestep per sample. This does not establish that the LSTM learned meaningful temporal dependencies.
4. **Synthetic target and features:** The dataset is simulated. Evaluation does not establish performance on operational Riyadh Metro data.

## Interpretation

The historical score is an outcome of the original classroom setup, **not a verified estimate of performance on live data**. The project remains useful as a working example of NLP input parsing, feature encoding, model training, and UI integration.

## Recommended independent re-evaluation

- Separate training, validation, and untouched test data **before** fitting transformations.
- Use a train-fitted `ColumnTransformer` or pipeline, with suitable encoders for categories.
- Compare with logistic regression and tree-based classification baselines.
- Inspect the simulated label-generation logic for trivial predictors or leakage.
- Report accuracy and macro-F1 with confusion matrices, alongside data limitations.
- If authentic ordered time series become available, evaluate on chronological splits and use a true multi-timestep model.

No new metric has been measured or claimed in this note.
