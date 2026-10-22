# Insiyab
**Riyadh Metro congestion classification prototype** · Academic AI project

Insiyab explores a natural-language interface for estimating station congestion levels. A user asks a question such as *"Is Al Batha crowded on Monday at 8 AM?"*; the prototype extracts trip details and maps them to a machine-learning classifier.

> **Important:** This is a demonstration trained on **synthetic metro data**, not live Riyadh Metro measurements. Predictions must not be interpreted as real transit conditions.

## Architecture

```text
User question
     |
     v
Trip-detail extraction (BART zero-shot + rules)
     |
     v
Station / weekday / time encodings
     |
     v
Classifier (LSTM-based notebook prototype)
     |
     v
Low / medium / high congestion (Gradio)
```

## Repository contents

| File | Description |
| --- | --- |
| [Prototype notebook](./Project_APP_Insiyab%20(1).ipynb) | Data exploration, model training, and Gradio integration |
| [Synthetic dataset](./Riyadh_Metro_Synthetic_10k.csv) | 10,000 simulated records used for the exercise |
| [Project report](./Insiyab_Report.pdf) | Coursework write-up |

**Stack:** Python · pandas · scikit-learn · TensorFlow/Keras · Hugging Face Transformers · Gradio

## Evaluation: important limitations

The original coursework report/README quoted approximately **95% accuracy**. Treat that as a **historical classroom result, not a validated generalization estimate**, because the notebook currently:

1. Fits a numerical scaler on the full dataset **before** splitting into training and test sets.
2. Uses the test split as `validation_data` during model training.
3. Feeds the LSTM a sequence length of **one timestep**, limiting its ability to model temporal sequences.
4. Trains entirely on simulated data.

A reliable new metric requires revising the experiment and rerunning it with a train-only preprocessing pipeline, separate validation/test splits, and suitable baseline models. No new performance result is claimed here.

## Running the prototype

The notebook was authored for Google Colab and expects the dataset at `/content/Riyadh_Metro_Synthetic_10k.csv`. It saves model and preprocessing artifacts during execution and loads them for Gradio inference later. Those generated artifacts are **not included** in this repository.

## Engineering upgrade plan

- Rebuild preprocessing as a leakage-safe scikit-learn pipeline.
- Compare appropriate tabular baselines against the LSTM approach.
- Introduce time-aware validation **if** a genuine temporal dataset becomes available.
- Package reusable inference code, tests, and a small API.
- Clearly distinguish simulated predictions from any future real-world integration.
