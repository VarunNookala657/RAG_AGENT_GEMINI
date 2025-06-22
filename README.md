# RAG_AGENT_GEMINI

# IPL 2025 RAG Agent with LangChain and Google Gemini

## Overview

This project demonstrates an AI agent powered by LangChain and Google Gemini, designed to answer questions about the **Indian Premier League (IPL) 2025**. The agent leverages **Retrieval-Augmented Generation (RAG)**, allowing it to fetch specific information from a predefined knowledge base (a Wikipedia article about IPL 2025) and use that context to formulate accurate and detailed responses.

## Key Features

* **Intelligent Agent:** Built with LangChain's AgentExecutor, capable of reasoning and deciding when to use external tools.
* **Retrieval-Augmented Generation (RAG):** Integrates a vector store (Chroma DB) and an embedding model (`models/embedding-001`) to retrieve relevant information from a knowledge base.
* **Custom Tool:** Defines a `get_ipl_2025_context` tool that the agent can call to query the IPL 2025 knowledge base.
* **Conversational Memory:** The agent maintains a memory of past interactions to provide more coherent responses.
* **Context-Awareness:** Demonstrates the agent's ability to discern when to use the RAG tool (for IPL 2025 questions) and when to rely on its general knowledge (for non-IPL questions).
* **Google Gemini Integration:** Utilizes Google's powerful Gemini LLM for reasoning and response generation.

## Project Structure

* `Gemini_Agentic_RAG.ipynb`: The main Jupyter Notebook containing all the code for setting up the environment, loading data, creating the vector store, defining the agent, and testing its capabilities.
* `requirements.txt`: Lists all Python dependencies required to run the notebook.

## How It Works

1.  **Data Loading:** The agent's knowledge base is derived from a Wikipedia article on the "2025 Indian Premier League".
2.  **Text Splitting:** The raw text is divided into smaller, manageable chunks to facilitate efficient retrieval.
3.  **Embedding Model:** Google's `models/embedding-001` is used to convert text chunks into numerical vector representations.
4.  **Vector Store (Chroma):** These embeddings are stored in a Chroma vector database, enabling semantic search.
5.  **Retriever:** A retriever is configured to fetch the most relevant text chunks based on a user's query.
6.  **Agent Definition:** An AI agent is created using LangChain's `AgentExecutor`, equipped with:
    * The `get_ipl_2025_context` tool, which wraps the retriever.
    * A custom prompt that guides the agent's reasoning and tool usage.
    * `GoogleGenerativeAI` (Gemini) as the underlying Large Language Model.
    * Conversational memory to maintain context across turns.
7.  **Querying:** When a user asks a question about IPL 2025, the agent intelligently decides to use the `get_ipl_2025_context` tool. The tool queries the vector store, retrieves relevant information, and passes it back to the LLM. The LLM then uses this retrieved context to formulate a precise answer. For general questions, the agent uses its internal knowledge.

## Setup and Installation

To run this project locally, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone [https://github.com/VarunNookala657/RAG_AGENT_GEMINI.git](https://github.com/VarunNookala657/RAG_AGENT_GEMINI.git)
    cd RAG_AGENT_GEMINI
    ```
2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate # On Windows: .\venv\Scripts\activate
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Set up your Google API Key:**
    * Obtain a Google API Key from [Google AI Studio](https://aistudio.google.com/app/apikey).
    * Set it as an environment variable (replace `YOUR_API_KEY`):
        ```bash
        export GOOGLE_API_KEY='YOUR_API_KEY'
        ```
        (For persistent setup, consider adding this to your `.bashrc` or `.zshrc` file, or load it within the notebook as shown in the project code.)
5.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook Gemini_Agentic_RAG.ipynb
    ```
    Follow the instructions within the notebook cells to execute the code step-by-step.

## Usage

Once the Jupyter Notebook is running and all cells are executed, you can interact with the agent by invoking `agent_executor.invoke()` with your questions within the notebook.

Example questions you can try:

* `"Who won the IPL 2025 tournament and where was the final played?"`
* `"Tell me about the key players and their performance for the IPL 2025 winning team."`
* `"What is the capital of France?"` (to test general knowledge routing)

## Future Enhancements

* Improve the prompt engineering for more robust answer extraction from retrieved context.
* Implement a reranking mechanism for retrieved documents to prioritize the most relevant information.
* Expand the knowledge base to include more comprehensive IPL data.
* Add a user interface (e.g., Gradio, Streamlit) for easier interaction.
* Incorporate more sophisticated memory management (e.g., summary memory, entity memory).

## Contributing

Feel free to open issues or submit pull requests if you have suggestions or improvements!

## License

This project is licensed under the [MIT License](LICENSE).

---
