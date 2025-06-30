# Emotion Detection with BERT (Multi-class Sentiment Analysis)
A real-time multi-class emotion detection system using BERT and Gradio. This project classifies text into emotions like happy, sad, angry, etc., and is ideal for applications in customer feedback, chatbots, social media analysis, and mental health tools.

# Objective
To fine-tune a pre-trained BERT model for emotion classification on text data, and deploy it through a user-friendly Gradio web app.

# Dataset
* Name: `smile-annotations-final.csv`
* Columns: `id`, `text`, `category`
* Preprocessing:
1. Filtered to six core emotions
2. Cleaned & normalized text
3. Encoded labels as integers for PyTorch
   
##  Workflow Summary

|   Step | Description                                                                 |
|--------|-----------------------------------------------------------------------------|
| 1️     | **Data Preprocessing**: Removed irrelevant classes, encoded labels, cleaned text |
| 2️     | **Split Dataset**: Stratified train-val split (85%-15%)                     |
| 3️     | **Tokenization**: Used `bert-base-uncased` tokenizer + padding + attention masks |
| 4️     | **Dataset Loader**: Created `PyTorch TensorDataset` for training            |
| 5️     | **Model Loading**: `BertForSequenceClassification` with 6-class output head |
| 6️     | **Training Loop**: 10 epochs, optimizer = `AdamW`, scheduler = linear warmup |
| 7️     | **Evaluation**: Calculated F1 Score, per-class accuracy, and loss           |
| 8️     | **Deployment**: Integrated with Gradio for real-time prediction interface   |

 Model Architecture
* Pre-trained BERT (bert-base-uncased) from Hugging Face
* Classification head with 6 output neurons (one for each emotion)
* *Loss Function*: `CrossEntropyLoss`
* Optimizer: `AdamW`
* Scheduler: Warm-up followed by linear decay
##  Evaluation Metrics (on Validation Set)

| Metric               | Value   |
|----------------------|---------|
| Weighted F1 Score    | 0.90    |
| Overall Accuracy     | 88.2%   |
| Loss (Validation)    | 0.36    |

##  Per-Class Accuracy

| Emotion   | Accuracy |
|-----------|----------|
| Happy     | 91%      |
| Sad       | 89%      |
| Angry     | 85%      |
| Fear      | 86%      |
| Surprise  | 88%      |
| Neutral   | 87%      |

## Sample Prediction
```
Text: "I can't stop smiling, today was amazing!"
→ Prediction: happy
```
