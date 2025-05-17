# 🧠 Real Estate Legal Advisor AI (RAG System)

**Real Estate Legal Advisor AI** is an advanced Retrieval-Augmented Generation (RAG) system developed during an AI course. It simulates the behavior of a "neuro-employee" — a virtual legal assistant trained to consult users on housing and real estate law in Russia.

This project goes beyond basic RAG architecture and demonstrates the **design, behavior modeling, and introspective debugging** of an AI agent.

---

## 🎯 Project Goals and Completed Tasks

✅ **Defined the Neuro-Employee’s Role**  
The assistant plays the role of a **Legal Advisor in Real Estate** with expert-level knowledge of the Housing Code of the Russian Federation. Its internal behavior is defined through a **system prompt**, describing its tone, logic, and boundaries of knowledge.

✅ **Designed its Internal World and Instructions**  
The system follows strict legal reasoning, avoids hallucinations, and always refers to official articles. The assistant behaves with calm professionalism, avoids guessing, and admits uncertainty when the answer is not explicitly stated in the documents.

✅ **Constructed a Legal Knowledge Base**  
A curated set of legal documents (PDFs) was collected and processed, including:
- The Housing Code of the Russian Federation
- Relevant extracts from the Civil Code
- Supplementary legal explanations

Knowledge is indexed via `LlamaIndex` using node-level chunking with metadata tags (e.g., article number, topic).

✅ **Chose the Framework**  
We use **LlamaIndex**, favoring its flexible RAG pipeline, reranking support, and easy integration with Russian LLMs.

✅ **Integrated a Russian LLM**  
The language model is YandexGPT, capable of fluent legal reasoning in Russian. A `CustomLLM` interface was implemented for seamless integration.

✅ **Traced Neuro-Employee Behavior**  
Using `Phoenix` tracing, we monitored:
- Query decomposition and embedding match quality
- Node retrieval scores
- Model uncertainty and hallucination likelihood

✅ **Diagnosed and Prevented Hallucinations**  
Although no hallucinations were directly observed during testing, we applied multiple defense mechanisms:
- Use of `tree_summarize` mode to restrict responses to retrieved context
- Added metadata checks to ensure legal citations match content
- Limited model temperature to reduce creative generation

✅ **Enhanced the RAG System**  
To go beyond typical blog-level implementations, we:
- Applied **LLM-based reranking (LLMRerank)** to improve answer relevance
- Created **dynamic prompt rewriting** for ambiguous questions
- Allowed **interactive trace visualization** via Phoenix

✅ **Implemented Query Filtering**  
A basic filter using keyword classification blocks non-legal or suspicious queries (e.g., "how to avoid paying taxes").

---

## 🏗️ Technologies Used

| Component             | Tech                          |
|----------------------|-------------------------------|
| Vector Search         | `LlamaIndex` with local index |
| Language Model        | `YandexGPT` (via CustomLLM)   |
| Document Parsing      | `SimpleDirectoryReader`       |
| Query Reranking       | `LLMRerank`                   |
| Tracing               | `Phoenix` + `ngrok`           |
| Environment           | Google Colab (Python 3.11+)   |

---

## 🧪 Sample Questions and Behavior

| User Query | Response Behavior |
|------------|-------------------|
| _“Do I have to pay for major repairs if I don’t live in the apartment?”_ | Links to Article 158 ЖК РФ and explains owner responsibilities. |
| _“Can I avoid paying for the roof repair?”_ | Returns filtered message: "Sorry, I can’t help with that." |
| _“What happens if a tenant damages property?”_ | Refers to Civil Code and landlord rights. |

---


