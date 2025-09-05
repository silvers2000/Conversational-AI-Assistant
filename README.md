# Conversational AI Assistant with RAG

This project is a sophisticated, multi-persona conversational AI assistant built using modern LLM frameworks. It's designed to be a versatile tool that can answer general questions and also function as an expert on specific documents provided by the user through a feature-rich Gradio web interface.

## 🚀 Key Features

* **Multi-Persona Chat:** Engage with different AI personalities, including a "Helpful Assistant," a "Sarcastic Teenager," and a "Wise Old Wizard."
* **Dynamic Tone Control:** Further refine the AI's responses by selecting a "Formal," "Friendly," or "Humorous" tone.
* **Retrieval-Augmented Generation (RAG):** Upload documents (`.pdf`, `.docx`, `.pptx`) and ask questions directly about their content. The AI uses the document as its primary source of knowledge.
* **Adjustable Creativity:** A "Temperature" slider in the UI allows for real-time control over the LLM's creativity versus predictability.
* **Stateful Conversations:** The assistant remembers the context of the ongoing conversation, allowing for natural back-and-forth dialogue.

## 🛠️ System Architecture & Technology Stack

The application is built on a modern, robust architecture designed for building advanced LLM applications.



* **UI Framework:** **Gradio** is used to create the interactive and user-friendly web interface.
* **Core Logic:** **LangGraph** serves as the backbone of the application, managing the agent's state and enabling complex, stateful conversational flows.
* **Large Language Model (LLM):** We utilize the **Llama 3.1 8B** model served via the **Groq API**, chosen for its exceptional speed and strong conversational capabilities.
* **Embeddings Model:** **`all-MiniLM-L6-v2`** from Hugging Face is used to create vector embeddings for the RAG pipeline. It runs locally, ensuring privacy and speed.
* **Vector Store:** **ChromaDB** is used as an in-memory vector database to store document chunks and perform efficient similarity searches for the RAG pipeline.

## ⚙️ Setup & Installation

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/silvers2000/Conversational-AI-Assistant.git](https://github.com/silvers2000/Conversational-AI-Assistant.git)
    cd Conversational-AI-Assistant
    ```

2.  **Create a `.env` file** in the root directory and add your secret API keys:
    ```
    GROQ_API_KEY="YOUR_GROQ_API_KEY"
    LANGCHAIN_TRACING_V2="true"
    LANGCHAIN_API_KEY="YOUR_LANGSMITH_API_KEY"
    ```

3.  **Install Dependencies:**
    It's recommended to use a virtual environment.
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Application:**
    Open and run the `main.ipynb` Jupyter Notebook. The Gradio application will launch and provide a local and public URL for you to interact with.

## 📊 RAG Pipeline Evaluation

To ensure the reliability and accuracy of our RAG system, we conducted a quantitative evaluation using the **Ragas** framework. We created a test dataset with a sample document (`project_apollo_overview.pdf`) and a set of question-answer pairs.

The evaluation measured four key metrics:

1.  **`context_recall`:** Measures whether the retriever successfully fetched all the relevant information from the document. **Our system achieved a perfect score of 1.0**, indicating flawless retrieval.
2.  **`answer_correctness`:** Measures how factually accurate the generated answer is compared to the ground truth. Our scores were high, demonstrating the LLM's ability to generate correct answers from the provided context.
3.  **`faithfulness`:** Measures if the answer is strictly based on the retrieved context, without making things up. Our model scored perfectly on this where applicable.
4.  **`answer_relevancy`:** Measures if the answer is relevant to the question.

#### Evaluation Results:
*(You can paste a screenshot of your Ragas evaluation table here if you'd like)*
```
--- RAG Evaluation Results ---
                                        question  ... answer_correctness
0       Who is the team lead for Project Apollo?  ...           0.851189
1  What is the primary objective of the project?  ...           0.912871
2  What is the codename of the assistant being...  ...           1.000000
3   Which LLM is used in the technology stack?    ...           0.987213
----------------------------
```
These results confirm that our RAG implementation is highly effective at both retrieving the correct information and using it to generate accurate answers.

## ιχ Tracing with LangSmith

As per the project guidelines, the application is fully integrated with **LangSmith** for LLM tracing. This allows us to monitor, debug, and evaluate every step of our RAG and agentic workflows.

