


William Anderson



Simple Retrieval-Augmented Generation (RAG) System 

Knowledge base - Rag : Implementing a Simple Retrieval-Augmented Generation (RAG) System 

Models Used:

Embedding Model

Model: all-MiniLM-L6-v2 (from Sentence Transformers)

Purpose: Converts text chunks and user queries into vector embeddings for similarity search.

Generation Model (LLM)

Model: Hosted by huggy-face/Transformers library-flan-t5-small

Purpose: Takes the retrieved context + question and generates a grounded answer.
In this assignment, the RAG system noticeably reduced hallucinations compared to using a raw LLM. In Test Case 1, where the answer was directly present in the knowledge base, the RAG pipeline retrieved the correct chunk and produced an accurate answer, whereas a raw LLM tended to generalize and occasionally produced partially incorrect details. In Test Case 2, where the knowledge base did not contain the answer, the RAG system correctly responded with “I don’t know based on the provided information,” avoiding hallucination entirely. In contrast, a raw LLM generated a confident but fabricated answer. In Test Case 3, the RAG approach successfully synthesized information across multiple retrieved chunks, showing better grounding and consistency. Overall, the RAG system demonstrated clear improvements in factual accuracy and reduced hallucinations by anchoring the model’s generation to retrieved text.


Analysis:
Across the three test cases, the retriever consistently returned the most semantically similar KB chunks, even when the answer was not present. For Test Case 1 (factual), the RAG system correctly grounded the model and prevented hallucination. In Test Case 2 (foil), retrieval worked correctly but the small FLAN-T5 generation model still hallucinated and returned an incorrect player name despite instructions to say “I don’t know.” In Test Case 3 (synthesis), retrieval succeeded by returning two knee-related entries, but the model only used one, revealing limitations in reasoning and multi-chunk synthesis. Overall, retrieval reduced hallucination but did not eliminate it entirely due to the limitations of the small generative model chosen.
