# ChatWithMultiplePDFS

Talking with multiple PDFS Documents using Google Gemini also using the LangChain and showcase how LangChain brought different ways of integrating.
Multiple PDFS converted to Vectors. After running the program we will get the fiass_index which will have the vector search similarity and the information will be stored in the database.
Create an API KEY from the Google AI Studio and provide that in .env file.

Flowchart :
Read PDFS using pdf reader -> Formulate the asked query -> Provide the response and related answer

Advantage : 
Can have any number of pdf with each pdf having size limit to maximum 200MB

Features : 
- Vector Embedding Technique -> FIASS
- LangChain

# Technology Used : 
1. FAISS -> Facebook AI Similarity Search -> This is used when we work with Vector Embedding we can even go for ChromaDB
2. LangChain
3. Python
4. Pdf Reader
5. GenAI
6. Streamlit

# Install the rquired packages / libraries :
```bash
pip install -r requirements.txt
pip install -U langchain-community
streamlit run app.py
```

# Overview :

https://github.com/user-attachments/assets/4b545736-983d-459d-9f4a-0ec866092c4e



