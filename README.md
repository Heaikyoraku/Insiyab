# Insiyab

<p><img src="https://skillicons.dev/icons?i=py,tensorflow,sklearn&theme=dark" alt="Python · TensorFlow · scikit-learn · NLP · LSTM · Gradio" height="34" /></p>
<sub>Python · TensorFlow · scikit-learn · NLP · LSTM · Gradio</sub>


**Natural-language metro congestion estimation — Riyadh**

Insiyab explores a conversational interface for asking about metro crowding. A user enters a question such as *“Is Al Batha crowded on Monday at 8 AM?”*; the workflow extracts station and time information and returns a predicted congestion category through Gradio.

## Flow

```text
Natural-language question
          |
          v
Trip details (BART zero-shot + parsing)
          |
          v
Encoded metro features
          |
          v
Trained classification model
          |
          v
Low / medium / high congestion
```

## Stack

`Python` · `pandas` · `TensorFlow/Keras` · `Hugging Face Transformers` · `scikit-learn` · `Gradio`

## Project files

| File | Description |
| :-- | :-- |
| [Application and training notebook](./Project_APP_Insiyab%20(1).ipynb) | Exploration, preprocessing, model training, inference, and Gradio |
| [Dataset](./Riyadh_Metro_Synthetic_10k.csv) | 10,000 simulated metro observations |
| [Technical report](./Insiyab_Report.pdf) | Original experiment and analysis |
| [Evaluation notes](./docs/evaluation-notes.md) | Methodology and interpretation of the reported score |

## Data and evaluation

The work uses **synthetic metro data**, not operational Riyadh Metro feeds. The original experiment reported ~95% classification accuracy, but its evaluation has methodological limitations documented [here](./docs/evaluation-notes.md); the figure should not be taken as verified real-world accuracy.

## Run

The notebook was created for Google Colab. Upload the CSV to `/content/`, run the training cells to generate model/preprocessing files, then run the Gradio interface cells.

<sub>Academic AI application focused on the ML-to-interface workflow.</sub>
