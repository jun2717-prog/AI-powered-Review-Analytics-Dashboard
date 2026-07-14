# AI-powered Review Analytics Dashboard

I built this as a personal portfolio project to go beyond a basic
sentiment classifier and put together a full AI application: a local ML
model doing the core work, a cloud LLM layered on top for a
conversational feature, and everything else — visualization, reporting,
deployment — that makes it a real, usable tool instead of just a script.

📁[Sample file to upload](sample_reviews_50_multilingual.csv) - multilingual 50 reviews 

🔗 **[Try it live](https://junio7191-sentiment-dashboard.hf.space)** — no installation needed


---

## Overview

Upload customer reviews — a single piece of text, a pasted list, or a
file — and get back sentiment classification, an aspect-level breakdown
(price, quality, delivery, etc.), visual charts, and an AI chat you can
ask questions about the results. Non-English reviews get translated
automatically. The core analysis runs entirely locally and for free; an
API key is only needed for translation and the chat.

## Features

- Sentiment classification (Positive / Neutral / Negative) with a
  confidence score per review
- Aspect breakdown across six categories: Price, Quality, Customer
  Service, Delivery, Functionality, Usability
- Automatic translation of non-English reviews, with the original text
  always preserved alongside
- **Ask AI** — a chat feature grounded in real computed statistics from
  the data, not just guesses from raw text
- Dashboard: sentiment charts, a weekly trend line, top keyword extraction
- Upload support for `.csv`, `.xlsx`, `.txt`, `.docx`, `.pdf`, `.json`,
  and images via OCR
- Export results to CSV or a formatted PDF report

## Tech Stack

Python · Gradio · Hugging Face Transformers (local sentiment model) ·
Google Gemini API (translation + chat) · pandas · Matplotlib/Plotly ·
Tesseract OCR · Hugging Face Spaces (hosting)

## How to Run

**Easiest way: just use the live demo above.**

To run it yourself:
```bash
git clone <this-repo-url>
cd <repo-folder>
pip install -r requirements.txt
python app.py
```
For translation and the Ask AI chat, get a free key at
[Google AI Studio](https://aistudio.google.com/apikey) and set it:
```bash
export GEMINI_API_KEY=your-key-here
```

## Downloaded PDF file with charts and graphs (Example)

[Sample report](sentiment_report.pdf)

## Known Limitations

- The app spots topics like price or quality by matching keywords, not
  with a dedicated AI model built for that — so it can miss reviews that
  hint at something without using the exact words.
- The "Ask AI" chat runs on a free service that only allows a limited
  number of questions per day.
- Translating reviews and using the AI chat both need a free API key;
  the main review analysis works without one.
- The AI chat finds relevant reviews by matching words, not by truly
  understanding meaning — so it can occasionally miss reviews that are
  related but worded differently.

## What I'd Improve Next

- Build a proper AI model for detecting review topics, instead of
  keyword matching.
- Make the AI chat understand meaning, not just matching words, when
  finding relevant reviews.
- Support more languages as the main analysis language, not just English.
