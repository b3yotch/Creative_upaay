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
