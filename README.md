


William Anderson / AD331
Knowledge base - Rag : Implementing a Simple Retrieval-Augmented Generation (RAG) System 

Models Used:

Embedding Model

Model: all-MiniLM-L6-v2 (from Sentence Transformers)

Purpose: Converts text chunks and user queries into vector embeddings for similarity search.

Generation Model (LLM)

Model: Hosted by huggy-face/Transformers library-flan-t5-small

Purpose: Takes the retrieved context + question and generates a grounded answer.
In this assignment, the RAG system noticeably reduced hallucinations compared to using a raw LLM. In Test Case 1, where the answer was directly present in the knowledge base, the RAG pipeline retrieved the correct chunk and produced an accurate answer, whereas a raw LLM tended to generalize and occasionally produced partially incorrect details. In Test Case 2, where the knowledge base did not contain the answer, the RAG system correctly responded with “I don’t know based on the provided information,” avoiding hallucination entirely. In contrast, a raw LLM generated a confident but fabricated answer. In Test Case 3, the RAG approach successfully synthesized information across multiple retrieved chunks, showing better grounding and consistency. Overall, the RAG system demonstrated clear improvements in factual accuracy and reduced hallucinations by anchoring the model’s generation to retrieved text.
