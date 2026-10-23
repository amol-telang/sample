# Website Chatbot

A Streamlit chatbot that reads a webpage and answers questions using its content.
It uses LangChain, Chroma for retrieval, and OpenAI for embeddings and chat
responses.

## Requirements

- Windows with Miniconda installed
- An OpenAI API key
- Python 3.10 in the `LangchainChatbot` Conda environment

## Install dependencies

Open PowerShell in this folder and activate the environment:

```powershell
conda activate LangchainChatbot
```

Install the app's packages:

```powershell
python -m pip install streamlit langchain langchain-community langchain-text-splitters langchain-openai chromadb python-dotenv beautifulsoup4
```

## Configure the OpenAI API key

The app accepts the key in its sidebar. Alternatively, create a `.env` file next
to `stramlit_run_app.py`:

```text
OPENAI_API_KEY=your-openai-api-key
```

Keep the key private. Do not commit the `.env` file to GitHub.

## Run the app

From this folder, run:

```powershell
python -m streamlit run stramlit_run_app.py
```

Open the local URL printed by Streamlit. Enter a webpage URL and OpenAI API key,
select **Read website**, and then ask questions in the chat.

## How it works

1. Loads the webpage's readable text.
2. Splits the text into overlapping chunks.
3. Creates embeddings and stores them in a Chroma vector store for the session.
4. Retrieves relevant excerpts to answer questions, using recent chat history
   to clarify follow-up questions.

The chatbot only uses the loaded webpage excerpts for answers. It reports when
it cannot find an answer in those excerpts.

## Notes

- The script filename is `stramlit_run_app.py` (including the spelling
  `stramlit`).
- The app needs an internet connection to read webpages and call OpenAI.
- The script uses the `gpt-4o-mini` chat model and `text-embedding-3-small`
  embeddings.
