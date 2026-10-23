# Document Chatbot

A Streamlit app that lets you upload documents and ask ChatGPT questions about
their contents.

## Supported files

- PDF
- Excel: `.xlsx`, `.xlsm`, `.xls`
- CSV and JSON
- Plain text: `.txt`, `.md`, `.log`
- Word: `.docx`
- PowerPoint: `.pptx`

Each file can be up to 20 MB. Scanned or image-only PDFs are not supported
because they require OCR.

## Requirements

- Python 3.10 or newer
- An OpenAI API key
- Internet access for OpenAI API requests

## Install

Open PowerShell in this folder and install the packages:

```powershell
python -m pip install -r requirements.txt
```

## Run

```powershell
python -m streamlit run document_chatbot.py
```

Open the local URL Streamlit prints. Enter your OpenAI API key in the sidebar,
upload files, select **Read documents**, then ask a question.

You can also set `OPENAI_API_KEY` in your environment instead of entering it
in the app. Never commit your key or a `.env` file containing it to GitHub.

## How answers are generated

The app extracts text from the uploaded files, selects relevant text excerpts
locally, and sends those excerpts and your question to OpenAI's `gpt-4o-mini`
model. Do not upload sensitive documents unless you are comfortable sharing
relevant excerpts with the OpenAI API.
