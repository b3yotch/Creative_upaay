# Intelligent Knowledge Extractor & Semantic Search for Content Discovery"

## About
This system is a **Retrieval-Augmented Generation (RAG)** pipeline enhanced with **Chain-of-Thought (CoT)** reasoning. It retrieves semantically relevant passages using FAISS, reranks them using Gemini 1.5 Pro, and applies a multi-step CoT reasoning chain to synthesize accurate, explainable answers tailored for student understanding.

## Approach
1. Data Ingestion :
i) collected article links from various sources particularly in AI domain
ii) extracted text along with the title while keeping the source link intact
iii) performed cleaning and preprocessing by removing the tags , punctuations,etc and creating a dictionary with title , source and cleaned_text 

2. Classification :
then classified the document in various domains of AI like ML, DL , Gen AI , Cv , NLP and others and stored each article in a data frame along with source , title and category

3. Summarization :
After classification did abstractive summarization using gemini as my motive is to create a system to assist students , thus making the summary more in human readable format
and then splitted into detailed and brief summary and stored in a json

5. Chunking :
created article chunks  with each chunk containing source link and title for efficient retrieval

6. Embedding :
then embeddings of chunks were created using 'gemini-embedding-exp-03-07' and these embeddings stored in faiss index along with metadata in a json file

 7. RAG System (Retrieval-Augmented Generation)
    When a user enters a query, the system follows a multi-stage pipeline to ensure accurate, context-rich, and pedagogically effective answers:
    
    i)Query Embedding
    The input query is embedded using the same Gemini embedding model (gemini-embedding-exp-03-07) to ensure vector space alignment with stored article chunks.
    
    ii)Semantic Retrieval via FAISS
    FAISS performs a fast similarity search over the stored chunk embeddings to retrieve the top-k most relevant text segments.
    
    iii)LLM-based Reranking (Gemini 1.5 Pro)
    Retrieved candidates are passed to Gemini 1.5 Pro, which reranks them based on contextual relevance to the query—this filters out noise and improves focus.
    
    iv)Answer Generation with Source-Aware Augmentation
    The top-ranked passages are passed along with the query to Gemini 1.5 Pro for answer synthesis. The system:
    
    Generates a detailed yet student-friendly response.
    
    Includes  article title and source URL along with relevance score.
    
    Highlights relevant excerpts from the original content.
    
    v)Chain-of-Thought (CoT) Reasoning
    The final answer incorporates multi-step reasoning to break down complex concepts—this improves transparency, educational value, and explainability.
