Project Title: Enhanced Agentic RAG for Document Retrieval and Summarization

Problem Statement:

Traditional Retrieval-Augmented Generation (RAG) pipelines often struggle with the retrieval of highly specific context from multiple documents, particularly when relying on a single LLM. Moreover, they may experience latency or failure due to rate limits from API calls, leading to an unreliable user experience. This project addresses these issues by integrating a multi-tool, agentic approach to improve query responses across multiple documents, with a particular focus on robustness, modularity, and adaptability.

Technology Stack:

	•	Python Libraries: llama-index, chromadb, faiss-cpu, sentence-transformers, gradio
	•	LLMs Used: Models such as llama3-8b-8192, gemma-7b-it, gemma2-9b-it
	•	Infrastructure: Hugging Face models, OpenAI API, Groq API for LLM execution
	•	Core Libraries:
	•	Llama-Index: For document indexing and retrieval
	•	Faiss: For fast similarity search
	•	ChromaDB: To manage and store embeddings efficiently
	•	Gradio: For an interactive user interface

Approach:

This project enhances the traditional RAG pipeline by introducing an agentic framework, allowing users to select from multiple Large Language Models (LLMs) dynamically based on their query requirements. The workflow involves:

	1.	Document Ingestion: Users upload multiple PDF files which are parsed and indexed using Llama-Index.
	2.	LLM Selection: Users select an appropriate LLM from a list of models (e.g., Llama3, Gemma, Mixtral) depending on the complexity and type of query.
	3.	Router-Based Query Engine: The system utilizes a RouterQueryEngine which employs a selector (LLMSingleSelector) to determine which LLM and query engine tool is best suited for the user’s input. This architecture supports both summarization and precise context retrieval from the uploaded documents.
	4.	Handling API Rate Limits: The project includes retry mechanisms (using tenacity) to mitigate rate limit errors from the OpenAI API, improving resilience during heavy query loads.

How It’s Better than a Normal RAG Pipeline:

	1.	Multi-LLM Flexibility: Unlike conventional RAG pipelines that use a single LLM, this solution allows users to choose from a range of models tailored to their specific needs, increasing response accuracy.
	2.	Modular Query Handling: The use of multiple query engines (summary and vector search tools) within the RouterQueryEngine enables more targeted and efficient queries.
	3.	Robust Error Handling: The integration of a retry mechanism with exponential backoff ensures smoother recovery from API rate limits, reducing downtime and improving user satisfaction.
	4.	Interactive UI: The Gradio interface provides an easy-to-use, interactive platform for users to upload documents, select models, and retrieve answers or summaries, making the tool accessible for non-technical users as well.

Usage Example:

	•	Upload multiple PDFs containing various types of documents (e.g., research papers, legal documents).
	•	Choose a Large Language Model that best suits your query (e.g., select a larger model for complex, cross-document reasoning).
	•	Ask questions related to specific documents or request document summaries. The system returns relevant text extracted from the indexed content using the chosen LLM.
