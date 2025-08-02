# Insiyab – Metro Congestion Prediction System

**Insiyab** is a smart AI-powered application that forecasts metro station crowding levels based on natural language queries. The project combines two powerful AI techniques:  
- A deep learning model (LSTM) trained on structured transit data  
- A pretrained NLP model (facebook/bart-large-mnli) for extracting trip details from plain English text  

The goal is to enhance urban mobility and support smart city initiatives by giving commuters real-time insights into metro congestion.

---

##  Features

- Accepts natural language input like:  
  _"Is Al Batha crowded on Monday at 8 AM?"_
- Converts text into structured data (station, day, time)
- Predicts crowd level: 🟢 Low, 🟡 Medium, 🔴 High
- Visual, user-friendly Gradio interface
- Built with synthetic data to simulate Riyadh Metro conditions

---

##  Project Files

- `Insiyab_Report.pdf`: Full academic report 
- `Project_APP_Insiyab(1).ipynb`: Jupyter Notebook with code (NLP + LSTM integration)
- `Riyadh_Metro_Synthetic_10k.csv`: The dataset generated using ChatGPT’s tools to simulate realistic scenarios

---

##  Tech Stack

- Python 3.10
- Gradio for UI
- Hugging Face Transformers (`facebook/bart-large-mnli`)
- TensorFlow/Keras (LSTM)
- Scikit-learn (evaluation metrics)

---

##  Model Performance

- **Accuracy**: 95% on test set  
- **Precision/Recall/F1**:
  - 🟢 Low: 0.94 / 1.00 / 0.97
  - 🟡 Medium: 0.92 / 1.00 / 0.96
  - 🔴 High: 1.00 / 0.84 / 0.91

---

##  Future Work

- Integrate with live metro APIs
- Add voice input support
- Improve recall for high congestion class
- Deploy as a mobile/web app

---

##  Dataset

Due to the lack of public metro data, a synthetic dataset was generated. You can find the `.csv` file included in this repo. It contains fields such as:
- Route ID
- Stations
- Hour, Day
- Peak Hour flag
- Passenger demand
- Congestion Level (target)

---

##  References

- [facebook/bart-large-mnli – Hugging Face](https://huggingface.co/facebook/bart-large-mnli)
- [Keras LSTM Documentation](https://keras.io/api/layers/recurrent_layers/lstm/)
- [Riyadh Metro Stations](https://rpt.sa/en/web/guest/routedetails?dir=H)

---

### 📌 Disclaimer

This is a university AI application project using synthetic data for research and prototyping purposes only.


