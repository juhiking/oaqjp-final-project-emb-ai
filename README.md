Final project

# Emotion Detection with Watson NLP

An AI-powered web application that analyzes customer feedback text and detects the underlying emotion — anger, disgust, fear, joy, or sadness — using IBM Watson NLP's Emotion Predict service. Built as the capstone project for the IBM "AI-Based Web Application Development and Deployment" course.

## Overview

This application was built for a fictional e-commerce company that wanted to run analytics on customer feedback for their products. It takes free-text input, sends it to the Watson NLP Emotion Predict API, and returns:

- A score (0–1) for each of the five core emotions
- The dominant (highest-scoring) emotion

The app is deployed as a Flask web service with a simple browser-based interface, includes unit tests, and passes static code analysis with a perfect PyLint score.

## Features

- **Emotion detection**: `emotion_detector()` sends text to Watson NLP and returns a structured dictionary of emotion scores and the dominant emotion.
- **Packaged application**: Core logic is packaged as the `EmotionDetection` Python package for clean, reusable imports.
- **Web deployment**: A Flask server (`server.py`) exposes the app via a `/emotionDetector` endpoint and a simple web UI.
- **Error handling**: Blank or invalid input is detected and handled gracefully, returning a clear error message instead of crashing.
- **Unit tested**: `test_emotion_detection.py` verifies the dominant emotion is correctly identified across all five emotion categories.
- **Clean code**: `server.py` scores 10/10 on PyLint static analysis, with docstrings throughout.

## Project Structure

```
oaqjp-final-project-emb-ai/
├── EmotionDetection/
│   ├── __init__.py            # Package init, imports emotion_detector
│   └── emotion_detection.py   # Core emotion detection logic
├── static/
│   └── mywebscript.js         # Front-end JS (provided)
├── templates/
│   └── index.html             # Web UI (provided)
├── test_emotion_detection.py  # Unit tests
├── server.py                  # Flask web server
├── README.md
└── LICENSE
```

## How It Works

1. A user enters text into the web form and submits it.
2. The Flask app (`server.py`) receives the text via the `/emotionDetector` route.
3. `emotion_detector()` sends the text to the Watson NLP Emotion Predict API.
4. The response is parsed into a dictionary of emotion scores, and the dominant emotion is calculated.
5. The result is formatted into a readable sentence and returned to the user.

Example response for the input *"I love this new technology."*:

```
For the given statement, the system response is 'anger': 0.0136, 'disgust': 0.0017,
'fear': 0.009, 'joy': 0.9719 and 'sadness': 0.0552. The dominant emotion is joy.
```

If the input is blank, the app responds with:

```
Invalid text! Please try again!
```

## Running Locally

> Note: This project relies on IBM's embeddable Watson NLP library, which is only accessible from within the IBM Skills Network Cloud IDE / Theia Lab environment.

1. Install dependencies:
   ```bash
   python3 -m pip install requests flask pylint
   ```
2. Run the unit tests:
   ```bash
   python3 test_emotion_detection.py
   ```
3. Start the web server:
   ```bash
   python3 server.py
   ```
4. Open the app in a browser at `http://localhost:5000`.

## Static Code Analysis

Run PyLint against the server code:

```bash
python3 -m pylint server.py
```

This project achieves a perfect **10.00/10** score.

## Author

Built by Juhi King as the final project for the IBM Developer Skills Network course *AI-Based Web Application Development and Deployment*.