# Chat With Multiple PDFs 🤖

## 📌 Introduction

**Chat With Multiple PDFs** is a Streamlit web application that lets users upload multiple PDF documents and ask natural language questions about their content. It uses **Google Gemini** for answer generation and **FAISS** vector search for relevant context retrieval, orchestrated through **LangChain**.

Uploaded PDFs are processed into text chunks, embedded using Google Generative AI embeddings, and stored in a local FAISS index. On each question, the app retrieves the most relevant chunks via similarity search and passes them to Gemini to generate a context-grounded answer.

**Key Features:**
- ✅ Upload any number of PDF files at once
- ✅ Extract full text from all pages using `PyPDF2`
- ✅ Split text into overlapping chunks with `RecursiveCharacterTextSplitter`
- ✅ Generate vector embeddings using `GoogleGenerativeAIEmbeddings`
- ✅ Store and search vectors locally with FAISS (`faiss_index/`)
- ✅ Answer questions using Google Gemini (`gemini-pro`) via LangChain QA chain
- ✅ Responds with "answer is not available in the context" when outside scope

---

## 🔄 Process / Flow

**Application Flow (`app.py`):**
1. User uploads PDF files via Streamlit sidebar
2. Click **Submit & Process** to trigger processing
3. Extract raw text from all uploaded PDF pages using `PdfReader`
4. Split text into chunks of 10,000 characters with 1,000 character overlap
5. Generate embeddings for each chunk using `GoogleGenerativeAIEmbeddings` (`models/embedding-001`)
6. Save embeddings to local FAISS index (`faiss_index/`)
7. User types a question in the main input box
8. Load FAISS index and run similarity search for relevant chunks
9. Pass retrieved chunks + user question into LangChain `load_qa_chain`
10. Gemini Pro generates a detailed answer from the retrieved context
11. Answer is displayed in the app with `st.write`

---

## 🛠️ Technology Used

| Component | Technology |
|-----------|-----------|
| **Language** | Python |
| **Web App** | Streamlit |
| **LLM** | Google Gemini Pro (`gemini-pro`) |
| **Embeddings** | Google Generative AI (`models/embedding-001`) |
| **Vector Store** | FAISS (Facebook AI Similarity Search) |
| **Orchestration** | LangChain (`load_qa_chain`, `PromptTemplate`) |
| **PDF Reader** | PyPDF2 |
| **Text Splitter** | `RecursiveCharacterTextSplitter` |
| **API Key Management** | `python-dotenv` |

---

## 🎓 Skills Gained

**LLM Application Development:**
- ✅ Building a Retrieval-Augmented Generation (RAG) pipeline
- ✅ Integrating Google Gemini via LangChain
- ✅ Custom prompt template design for context-grounded answers

**Vector Search & Embeddings:**
- ✅ Generating text embeddings with Google Generative AI
- ✅ Storing and querying embeddings with FAISS
- ✅ Similarity search for relevant document retrieval

**Document Processing:**
- ✅ Multi-PDF text extraction using PyPDF2
- ✅ Chunking with overlap using `RecursiveCharacterTextSplitter`

**Deployment & Integration:**
- ✅ Streamlit multi-page UI with sidebar file upload
- ✅ API key management with `.env` and `python-dotenv`

---

## 📂 Project Structure

```
ChatWithMultiplePDFS/
├── app.py              # Main Streamlit app: PDF processing, FAISS indexing, QA chain
├── requirements.txt    # Python library dependencies
├── README.md           # Project documentation
└── faiss_index/
    └── index.faiss     # Saved FAISS vector index (generated after processing PDFs)
```

---

## 📸 Demonstration

https://github.com/user-attachments/assets/4b545736-983d-459d-9f4a-0ec866092c4e

---

## ⚙️ Setup Instructions

### Prerequisites:
- Python 3.x
- Google AI Studio account with a Gemini API key

### Step-by-Step Installation:

**1. Clone the Repository**
```bash
git clone <your-repo-url>
cd ChatWithMultiplePDFS-main
```

**2. Install Dependencies**
```bash
pip install -r requirements.txt
pip install -U langchain-community
```

**3. Create API Key**
- Go to [Google AI Studio](https://aistudio.google.com/)
- Generate an API key

**4. Set Up Environment Variables**
Create a `.env` file in the project root:
```
GOOGLE_API_KEY=your_api_key_here
```

**5. Run the App**
```bash
streamlit run app.py
```

**6. Use the App**
- Upload one or more PDF files in the sidebar
- Click **Submit & Process** to build the FAISS index
- Type a question in the main input to get a context-grounded answer
