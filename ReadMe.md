# RAG-based Chatbot using LangChain & ChromaDB

### This project is a Retrieval-Augmented Generation (RAG) chatbot.
It uses LangChain, ChromaDB, and OpenAI embeddings to load documents (e.g., announcements, notices), split them into chunks, store them in a vector database, and then answer student queries in a formal manner.

## 🚀 Features

- Load .txt files as knowledge base documents.

- Split documents into smaller chunks for better embedding retrieval.

- Store embeddings in ChromaDB for persistent querying.

- Query the chatbot with natural language questions.

- Returns both answers and sources.

## 🛠️ Requirements

The project runs in Google Colab. You need:

- A Google account.

- An OpenAI API key (to generate embeddings and run ChatGPT model).

    Get it from: [OpenAI API Keys]((https://platform.openai.com/account/api-keys))

## ⚙️ Setup & Installation (Colab)

Follow these steps in Google Colab:

### 1. Clone or upload the notebook

Upload the provided lpu_query_bot.ipynb to your Google Drive or open it directly in Google Colab.

### 2. Install dependencies

Run the first cell to install required libraries:
```bash
!pip install tiktoken
!pip install langchain_community
!pip install langchain
!pip install unstructured
!pip install openai
!pip install chromadb
```
Note : Run each cell in order otherwise it will throw an error.

### 3. Set environment variables

Replace with your OpenAI API key:
```python
os.environ['OPENAI_API_KEY'] = 'your_openai_api_key_here'
CHROMA_PATH = "/content/chroma_db"
DATA_PATH = "/content/data"
```

### 4. Add documents

Upload your .txt files inside the /content/data directory.

Example:
```bash
/content/data/Announcements.txt
/content/data/Exam_Notices.txt
```

### 5. Generate the vector database

Run the cell containing:
```python
main()
```
This will:

- Load all .txt files.

- Split them into chunks.

- Save them in ChromaDB.


### 6. Query the chatbot

Update the query text:
```python
query_text = "Is there any announcement regarding reappear?"
```
Run the cell with the chatbot logic. It will return:
- ✅ Formal Answer
- 📌 Sources from which the answer was derived


### Example Output
```vbnet
Response: Yes, there is an announcement regarding the Reappear/Improvement Examination 2324B...
Sources: ['/content/data/Announcements.txt']
```

### 🧩 Customization

- Change query_text to ask different questions.

- Add more .txt files in the /content/data/ folder to expand knowledge.

- Adjust chunk size/overlap in RecursiveCharacterTextSplitter for different document types.

### 📝 Notes

- This is a prototype RAG chatbot. It works best when documents are well-structured text.

- For PDFs, CSVs, or other formats, additional loaders from langchain_community.document_loaders can be used.