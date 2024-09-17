# Gen AI Engineer / Machine Learning Engineer Assignment

## Overview

This project involves the development of a **Retrieval-Augmented Generation (RAG) model** for a Question Answering (QA) bot, aimed at enhancing information retrieval from documents using generative AI. The project is divided into two main parts: implementing a RAG-based model and creating an interactive interface to query the bot in real-time.

## Table of Contents
1. [Part 1: Retrieval-Augmented Generation (RAG) Model](#part-1-retrieval-augmented-generation-rag-model)
    - Problem Statement
    - Approach
    - Features
    - Dependencies
    - How to Run the Colab Notebook
2. [Part 2: Interactive QA Bot Interface](#part-2-interactive-qa-bot-interface)
    - Problem Statement
    - Approach
    - Features
    - How to Run the Interface
3. [General Guidelines](#general-guidelines)
4. [Deployment Instructions](#deployment-instructions)
5. [Example Queries and Outputs](#example-queries-and-outputs)
6. [Challenges and Solutions](#challenges-and-solutions)
7. [Future Work](#future-work)

---

## Part 1: Retrieval-Augmented Generation (RAG) Model

### Problem Statement
The goal is to create a RAG-based model capable of answering questions from users by retrieving information from a provided dataset or document. The model combines a **retrieval mechanism** (using vector databases like Pinecone) with a **generative model** (such as Cohere API) to produce accurate, contextually relevant answers.

### Approach
1. **Data Processing**: 
   - Load the document or dataset and preprocess it for embeddings.
   - Convert the document into vectors using sentence transformers or embeddings provided by Cohere or another API.
   
2. **Retrieval Mechanism**:
   - Use **Pinecone DB** to store the embeddings of the document and retrieve the most relevant segments in response to user queries.
   
3. **Generative Model**:
   - Once the relevant document sections are retrieved, the generative model formulates a coherent and accurate answer.

### Features
- **Document Embedding**: Efficient storage and retrieval using Pinecone or another vector database.
- **Generative Response**: Uses an API like Cohere to create human-like responses based on retrieved information.
- **Query Testing**: Demonstrates how the model can handle multiple queries and provide accurate answers.

### Dependencies
- Python 3.7+
- Colab Notebook (Google Colab)
- Pinecone (for vector database)
- Cohere API (or other generative model alternatives)
- Required Libraries: `sentence-transformers`, `pytorch`, `transformers`, `pinecone-client`, `cohere` (or GPT alternatives)

### How to Run the Colab Notebook
1. Open the Colab notebook link provided in the repository.
2. Install the required dependencies:
    ```bash
    !pip install sentence-transformers cohere pinecone-client transformers
    ```
3. Load your dataset/document for embedding.
4. Follow the steps to run the retrieval and generative model queries.
5. Test queries as shown in the example section.

---

## Part 2: Interactive QA Bot Interface

### Problem Statement
The aim is to create an interactive, user-friendly interface where users can upload documents and ask questions based on their content. This part builds on the backend model developed in Part 1 and allows real-time interaction through a web-based frontend.

### Approach
1. **Frontend Development**: 
   - Develop a user interface using **Streamlit** or **Gradio**.
   - Allow users to upload documents in PDF format and submit queries.
   
2. **Backend Integration**:
   - Use the RAG model from Part 1 to process the uploaded document, store embeddings, and retrieve answers to user queries in real-time.

3. **Real-Time Interaction**:
   - The system efficiently handles multiple queries and shows the retrieved document segments alongside the generated answers.

### Features
- **File Upload**: Allows users to upload PDF documents.
- **Real-time QA**: Users can ask questions based on the uploaded document's content.
- **Generated Answer with Context**: Displays retrieved document segments with the generative answer.
- **Scalability**: Can handle multiple queries with large documents.

### How to Run the Interface
1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo-url.git
    ```
2. Navigate to the project directory:
    ```bash
    cd your-repo-directory
    ```
3. Install required libraries:
    ```bash
    pip install streamlit gradio pinecone-client cohere
    ```
4. Run the interface:
    ```bash
    streamlit run app.py
    ```
5. Interact with the bot by uploading documents and asking questions.

---

## General Guidelines

1. **Modular Code**: The code is divided into reusable functions for document processing, retrieval, and answer generation.
2. **Scalable System**: Both backend and frontend components are scalable and can handle large datasets/documents efficiently.
3. **Detailed Documentation**: Each part of the codebase is well-documented for clarity, covering everything from data loading to query answering.

---

## Deployment Instructions

The application is containerized using Docker for easy deployment.

### Steps:
1. Build the Docker container:
    ```bash
    docker build -t qa-bot-app .
    ```
2. Run the container:
    ```bash
    docker run -p 8501:8501 qa-bot-app
    ```
3. Access the app through your browser at `http://localhost:8501`.

---

## Example Queries and Outputs

### Example 1:
**Question**: "What is the annual revenue of the business in 2022?"

**Generated Answer**: "The business generated $5 million in revenue in 2022, according to the provided financial report."

**Retrieved Document Section**: "...in the year 2022, the total revenue of the business amounted to $5 million..."

### Example 2:
**Question**: "What are the benefits of the new product?"

**Generated Answer**: "The new product offers improved efficiency and user-friendly features, as highlighted in the product description."

---

## Challenges and Solutions

- **Embedding Large Documents**: Used Pinecone for efficient embedding and retrieval of large document sections.
- **Performance Bottleneck**: Optimized document chunking and retrieval to ensure smooth performance with multiple queries.

---

## Future Work

- **Advanced QA Features**: Incorporate support for more complex queries and document analysis.
- **Model Fine-tuning**: Experiment with different generative models and fine-tune for domain-specific applications.
- **Improved UI**: Enhance the user interface for better user experience and additional functionalities.
