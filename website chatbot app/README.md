# Website and Document Chatbots

This repository contains Streamlit apps that use OpenAI to answer questions
about webpages or uploaded files.

## Requirements

- Python 3.10 or newer
- An OpenAI API key
- Internet access for OpenAI API requests

Install the dependencies from this folder:

```powershell
python -m pip install -r requirements.txt
```

The app prompts for an OpenAI API key in its sidebar. Alternatively, set
`OPENAI_API_KEY` in your environment or in a local `.env` file. Never commit
your API key or `.env` file to GitHub.

## Document chatbot

Run the document Q&A app:

```powershell
python -m streamlit run document_chatbot.py
```

Upload documents in the sidebar, click **Read documents**, then ask questions.
Supported formats are PDF, Excel (`.xlsx`, `.xlsm`, `.xls`), CSV, JSON, TXT,
Markdown, LOG, Word (`.docx`), and PowerPoint (`.pptx`). Files are limited to
20 MB each. Scanned or image-only PDFs need OCR and are not supported.

The app extracts and ranks relevant text excerpts locally, then sends those
excerpts and your question to OpenAI to generate an answer. Do not upload
sensitive documents unless you are comfortable sharing relevant excerpts with
the OpenAI API.

## Website chatbot

Run the website Q&A app:

```powershell
python -m streamlit run website_chatbot.py
```

Enter a webpage URL, click **Read website**, then ask questions about its text.
The app reads regular HTML pages; sites that require JavaScript or block
automated requests may not load.

The original LangChain website chatbot is also available:

```powershell
python -m streamlit run stramlit_run_app.py
```

## Notes

- Streamlit prints a local URL when an app starts; open it in your browser.
- `stramlit_run_app.py` keeps its original filename spelling.
- The apps use the `gpt-4o-mini` model. The original LangChain app also uses
  `text-embedding-3-small` embeddings.
