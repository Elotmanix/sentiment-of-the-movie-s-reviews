

# Sentiment Model API

This project is a simple API for predicting the sentiment (positive or negative) of movie reviews using Natural Language Processing (NLP). The API uses a pre-trained sentiment analysis model to process movie review texts and return the predicted sentiment along with the probability score.

## Features

- **Text Preprocessing:** The API cleans and processes the input text by tokenizing, removing stop words, lemmatizing, and removing punctuation and numbers.
- **Sentiment Prediction:** Uses a pre-trained model to predict the sentiment of a movie review (positive or negative).
- **FastAPI:** FastAPI framework for creating the API endpoints.
- **CORS Middleware:** Configured to allow cross-origin requests from any domain.

## Installation

### Prerequisites

- **Python 3.8+**
- **FastAPI**
- **Joblib** (for loading the pre-trained model)
- **NLTK** (for text preprocessing)
- **Uvicorn** (ASGI server for FastAPI)
  
### Required Libraries

Install the required Python libraries using `pip`:

```bash
pip install fastapi uvicorn joblib nltk
```

### NLTK Setup

Make sure to download the necessary NLTK data for stopwords and tokenization:

```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

### Folder Structure

Ensure the following project structure:

```
.
├── app.py                   # Main application file
├── sentiment_model_pipeline.pkl  # Pre-trained model
└── static
    └── index.html            # Frontend file for the main page (if applicable)
```

## How to Run

1. **Start the API server**:
   
   Run the FastAPI application using Uvicorn:

   ```bash
   uvicorn app:app --reload
   ```

2. **Access the API**:
   
   The API will be available at `http://127.0.0.1:8000`.

3. **Endpoints**:

   - **GET /**:
     - Description: Returns the main page (`index.html`).
   - **POST /predict-review**:
     - Description: Takes a movie review as input and returns the sentiment (positive/negative) and the associated probability.
     - Request Example:
       ```bash
       curl -X 'POST' \
       'http://127.0.0.1:8000/predict-review' \
       -d "review=This movie was fantastic!"
       ```
     - Response Example:
       ```json
       {
         "prediction": "Positive",
         "Probability": "0.85"
       }
       ```

## Project Details

- **Text Preprocessing**: The API cleans the text by removing punctuation, stopwords, and numbers, and then lemmatizes the words for better sentiment prediction.
  
- **Sentiment Model**: The pre-trained model (`sentiment_model_pipeline.pkl`) is loaded using `joblib` and is used to predict sentiment from cleaned reviews.

- **CORS Middleware**: The app is set up to allow requests from any domain, but this can be adjusted in the `app.add_middleware` section in `app.py`.

## Future Enhancements

- Add more sophisticated text preprocessing techniques.
- Improve model prediction accuracy with a larger or more fine-tuned dataset.
- Implement additional endpoints for batch predictions.

