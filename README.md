# Multi-Agent Retreival Augemented Generation (MARAG) System

## Overview

This project implements a Multi-Agent Retrieval-Augmented Generation (RAG) system. Unlike traditional RAG systems that use a single context retrieval and generation mechanism, this multi-agent system leverages multiple contexts and specialized agents to provide a comprehensive and accurate final answer. The system decomposes the input question into multiple contexts, retrieves relevant information for each context, and synthesizes the results from multiple agents to produce a final answer. The document used to answer questions is the following blog - https://lilianweng.github.io/posts/2023-06-23-agent/

## Libraries Used

### 1. `bs4`
* **Description**: BeautifulSoup4 is a library for parsing HTML and XML documents.
* **Usage**: It is used to parse and extract content from web pages, specifically targeting the parts of the document that contain relevant information.

### 2. `langchain`
* **Description**: LangChain is a library for building language model applications.
* **Usage**: Provides the core framework and tools to define and run language model-based agents and pipelines.

### 3. `langchain_community.document_loaders`
* **Description**: A module within LangChain for loading documents from various sources.
* **Usage**: Used to load and preprocess content from web pages.

### 4. `langchain_chroma`
* **Description**: Chroma is a library for vectorizing and indexing documents.
* **Usage**: Used for creating vector embeddings of the document chunks and facilitating efficient retrieval of relevant chunks.

### 5. `langchain_core.output_parsers`
* **Description**: Provides utilities for parsing the output of language models.
* **Usage**: Used to structure and format the output generated by the language models.

### 6. `langchain_core.runnables`
* **Description**: Core utilities for building runnable tasks in LangChain.
* **Usage**: Provides the functionality to create and manage the runnable tasks that form the building blocks of the multi-agent system.

### 7. `langchain_openai`
* **Description**: LangChain integration for OpenAI language models.
* **Usage**: Facilitates the use of OpenAI’s language models for generating responses based on retrieved contexts.

### 8. `langchain_text_splitters`
* **Description**: A module for splitting large documents into manageable chunks.
* **Usage**: Used to split the documents into smaller, overlapping chunks to optimize the retrieval process.

## System Functioning

### Initialization
1. **Loading and Parsing Documents**: The system loads and parses documents from specified web paths using `WebBaseLoader` and `BeautifulSoup`.
2. **Chunking and Vectorizing**: The parsed documents are split into chunks using `RecursiveCharacterTextSplitter` and vectorized using `Chroma` with `OpenAIEmbeddings`.

### Multi-Agent Mechanism
1. **Context Identification**: The input question is analyzed to identify five distinct contexts.
2. **Agent Creation**: For each context, a specialized agent is created. Each agent retrieves relevant document chunks specific to its context.
3. **LLM Invocation**: Each agent calls the LLM with its retrieved context to generate a response.
4. **Aggregation**: The responses from all agents are aggregated to form the final answer.

## Advantages Over Single RAG System

1. **Context Diversity**: By decomposing the question into multiple contexts, the system captures a broader range of relevant information.
2. **Specialized Retrieval**: Each agent focuses on a specific aspect of the question, leading to more precise retrieval and response generation.
3. **Comprehensive Answers**: The final aggregation of multiple agent responses ensures a more thorough and nuanced answer, reducing the likelihood of missing critical information.

This multi-agent approach enhances the traditional RAG system by leveraging the strengths of multiple specialized agents, resulting in more accurate and comprehensive answers.

