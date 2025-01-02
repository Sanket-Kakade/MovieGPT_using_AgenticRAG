# MovieGPT_using_AgenticRAG
An LLM answering the question on Indian cinema. 

This project demonstrates an advanced question-answering system using Retrieval Augmented Generation (RAG) and a state graph.  It leverages a vector database built from the IMDb-Media dataset, focusing on Indian movies.  The system incorporates several key features:

* **Vector Database:**  A Chroma vector database stores embeddings of movie details (title, storyline, genre, etc.) generated using HuggingFace embeddings (BAAI/bge-large-en-v1.5). This allows for efficient similarity search based on user queries.
* **Multi-stage Retrieval:**  The system uses a state graph to manage the retrieval process. It first queries the vector database, then assesses the relevance of retrieved documents using an LLM grader (llama3-8b-8192). If relevant documents are lacking, the query is rephrased and a web search (Tavily Search) is conducted.
* **LLM-powered Grader and Rephraser:**  An LLM acts as a document grader, filtering out irrelevant results from the vector database. Another LLM rephrases user queries for improved search performance, especially when web search is necessary.
* **RAG Pipeline:**  A RAG pipeline combines relevant context documents (from the database or web search) with a user's question and feeds them to a large language model (llama3-70b-8192) for answer generation.
* **Hybrid Search:** Combines vector database search with web search to handle queries not covered in the initial dataset.

The code provides several examples of using the system to answer questions about Indian movies, including suggestions, story summaries, and searches for specific criteria.  The system is designed to be robust, handling both in-scope and out-of-scope queries effectively.

The project utilizes several libraries, including `langchain`, `datasets`, `sentence-transformers`, `InstructorEmbedding`, and `chromadb`.  API keys for OpenAI (or Groq), and Tavily are required to run the code.
