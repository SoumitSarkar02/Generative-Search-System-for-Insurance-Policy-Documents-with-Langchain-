# Generative Search System for Insurance Policies

## 📌 Project Overview
This project is a **Retrieval-Augmented Generation (RAG) based AI system** that allows users to ask questions about insurance policy documents and get **accurate, contextual responses** using **LangChain**, **OpenAI GPT-4o**, and **ChromaDB**.

## 🚀 Features
- **Document Parsing:** Extracts and processes text from multiple insurance policy PDFs.
- **Chunking:** Breaks down large documents into meaningful chunks for better retrieval.
- **Embedding Generation and Caching:** Converts text into vector embeddings using OpenAI and cache them.
- **Vector Storage:** Stores embeddings in **ChromaDB** for fast similarity search.
- **Retriever with Re-Ranking:** Uses **MMR-based retrieval** and **Cross Encoder Re-ranking** for high-precision document retrieval.
- **RAG Pipeline:** Combines retrieved documents with **gpt-4o-mini** to generate **context-aware answers.**

## 📦 Installation
Ensure you have **Python 3.8+** installed. Then, install the required dependencies:
```bash
pip install langchain langchain-core langchain-community chromadb openai tiktoken
huggingface_hub pypdf
```

## ⚙️ Setup
1. **Set Up OpenAI API Key**
   ```python
   import os
   os.environ["OPENAI_API_KEY"] = "your_openai_api_key_here"
   ```
2. **Store PDF Files** in a local directory (e.g., `./data/`) or Google Drive.
3. **Run the pipeline step by step in a Jupyter Notebook or Google Colab.**

## ▶️ How to Run the Application
1. **Extract Text from PDFs**
   ```python
   extracted_text = extract_text_from_pdfs(pdf_files, pdf_folder)
   ```
2. **Chunk the Documents**
   ```python
   chunked_documents = chunk_documents(extracted_text)
   ```
3. **Generate & Cache Embeddings**
   ```python
   embeddings = generate_embeddings(chunked_documents)
   ```
4. **Store in ChromaDB**
   ```python
   chroma_db = Chroma.from_documents(documents=documents,  embedding=embedding_function)
   ```
5. **Retrieve Relevant Chunks & Generate Answers**
   ```python
   test_query = "What is the minimum age for term insurance?"
   response = rag_chain.invoke(test_query)
   print(response)
   ```

## 📝 Sample Queries
```python
queries = [
    "What are the exclusions in the insurance policy?",
    "What is the minimum age for doing a term insurance?",
    "What is criteria for HDFC group insurance?",
    "What are the benifits of HDFC Sampoorna-Jeevan insurance?",
    "Can a 100-year-plus person do a term insurance?",
    "What is the condition of death while not wearing a seat belt?",
]

for query in queries:
  print(f"Query: {query}")
  response = rag_chain.invoke(query)
  print("Generated Answer:")
  print(response)
  print("-" * 80)

```

## ❓ Troubleshooting
- **Missing API Key Error:** Ensure your OpenAI API key is set as an environment variable.
- **Embeddings Not Found:** Re-run the **generate & store embeddings** step before querying.
- **Slow Retrieval:** Reduce `topk` in the retriever settings for faster responses.

## 💡 Future Enhancements
- **Multi-Language Support**: Expand to process and retrieve policies in multiple languages.
- **Fine-Tuning**: Customize the LLM for domain-specific terminology.
- **Web Interface**: Develop a UI for easy interaction with the model.

## 📜 License
This project is open-source under the **MIT License**.

---
### **🔹 Built with LangChain, OpenAI, ChromaDB & Python** 🔹


