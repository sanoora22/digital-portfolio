Citizen AI

An AI-powered assistant that combines city safety analysis with a citizen services chatbot, built using IBM's Granite large language model and served through an interactive Gradio interface.

Overview

Citizen AI has two core capabilities:


City Analysis — enter any city name and get an AI-generated breakdown covering crime index, safety statistics, accident rates, and an overall safety assessment.
Citizen Services Assistant — ask questions about public services, government policies, or civic issues and receive AI-generated, government-assistant-style responses.


The app runs on the ibm-granite/granite-3.2-2b-instruct model and is served through a two-tab Gradio web interface, so it can run in a notebook (originally built and run on Google Colab) or locally with GPU/CPU support.

Features


Natural language city safety analysis (crime index, accident rates, safety summary)
Citizen query assistant for public service and civic-issue questions
Powered by IBM Granite 3.2 (2B instruct) via Hugging Face Transformers
GPU-aware inference (automatically uses CUDA if available, falls back to CPU)
Simple, tabbed Gradio UI — no frontend code required
Shareable public link via app.launch(share=True)


Tech Stack


Language: Python
ML/LLM: Hugging Face Transformers, PyTorch, IBM Granite 3.2-2B-Instruct
Interface: Gradio


How It Works


The Granite model and tokenizer are loaded from Hugging Face on startup
User input (a city name or a citizen query) is wrapped in a structured prompt
The prompt is passed to the model, which generates a response via sampling (temperature=0.7)
The generated text is cleaned up and displayed in the Gradio output box
Two tabs keep the two use cases (city analysis vs. citizen services) separate but built on the same underlying generation pipeline


Getting Started

Prerequisites


Python 3.x
pip


Installation

bashgit clone https://github.com/sanoora22/citizen-AI.git
cd citizen-AI
pip install transformers torch gradio
python citizen_ai.py


Note: The model will download automatically from Hugging Face on first run. A GPU is recommended for faster inference, but the app will run on CPU as well.



Usage

Once running, Gradio will print a local (and optionally public, via share=True) URL. Open it in a browser and:


Use the City Analysis tab to enter a city name and get a safety/crime overview
Use the Citizen Services tab to ask a question about public services or civic issues


Project Structure

citizen-AI/
├── citizen_ai.py          # Main application: model loading, generation logic, Gradio UI
├── citizen AI doc.pdf     # Project documentation
├── citizen AI voiceover.mp4  # Project walkthrough/demo
└── README.md

Future Improvements


Add caching to avoid reloading the model on every session
Add source citations or a retrieval step to ground city safety claims in real data
Deploy as a persistent hosted app (e.g., Hugging Face Spaces) instead of Colab-based sharing
Add input validation and error handling for unsupported or ambiguous city names


