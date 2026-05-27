# 🪄 Agentic RAG Panel
  **Multilingual Web-Scraping & QA Engine (Jupyter Edition)** 

  This repo is an advanced, production-grade Retrieval-Augmented Generation (RAG) system built entirely within Jupyter Notebooks. It bridges the gap between raw web data and structured AI reasoning, offering a highly **interactive** UI with dynamic state management.

<img width="1305" height="637" alt="Screenshot 2026-05-27 022116" src="https://github.com/user-attachments/assets/6938480a-e51e-4956-b7ea-bef2f497a943" />
<img width="1321" height="712" alt="Screenshot 2026-05-27 022222" src="https://github.com/user-attachments/assets/61d740d3-6157-49d6-bd07-b0854aea8416" />

  ---

  ## 🏗️ System Architecture & Enhancements
  Built to bypass traditional scraping limitations, the architecture focuses on a "Universal Extraction" philosophy, ensuring high-quality context delivery to the LLM regardless of the source language or website structure.

  ### 1. Core Foundations
  * **Resilient Web Crawler:** A custom `advanced_web_scraper` that injects professional Headers and autonomously decomposes irrelevant DOM elements (navbars, footers, scripts, forms) to extract pure, meaningful text and tables.
  * **Semantic Vector Space:** Leverages the `paraphrase-multilingual-MiniLM-L12-v2` embedding model, allowing the system to map both Persian (RTL) and English (LTR) text uniformly without translation loss.
  * **Dynamic State Machine:** Replaces linear cell execution with an event-driven `ipywidgets` architecture, managing UI states seamlessly without kernel restarts.
  * **Robust Data Pipeline:** Employs Langchain's `RecursiveCharacterTextSplitter` with specialized separators (including Persian commas) to maintain context overlap during chunking.

  ---

  ## 🛠️ Main Features & Services

  ### 🌐 Universal Bilingual Support
  * **Native RTL/LTR Rendering:** The UI automatically detects language constraints. Persian responses are rendered strictly right-to-left with proper typography, while English follows left-to-right conventions.
  * **Intelligent Markdown Parser:** LLM responses are parsed through a custom CSS layer (`.markdown-rtl`) that fixes common rendering issues with bullet points and bold text in Persian.

  ### 🧠 Advanced Context Handling
  * **High-Density Retrieval:** Queries ChromaDB for `n_results=10` to ensure no critical information (like specifications hidden in deep tables) is missed during the generation phase.
  * **Anti-Hallucination Prompting:** Strict system instructions force the LLM to admit "Insufficient information" if the exact answer is not present in the extracted chunks.

  ---

  ## 💎 UI/UX & Interactive Features

  ### 🎨 The "App-in-a-Notebook" Experience
  * **Widget-Based Dashboard:** Replaces standard `print()` outputs with a rich, responsive interface featuring input fields, dropdowns, and distinct action buttons styled with Bootstrap color schemes (`primary`, `success`, `warning`, `info`).
  * **Chunk Inspection Box:** A dedicated container that allows users to audit the exact data extracted from the webpage before querying the LLM.

  ### 🗃️ Session Management & Export
  * **Stateful Execution:** Users can process multiple URLs and ask sequential questions within a single session using the *Reset Session* feature, which safely clears the database and UI state.
  * **One-Click CSV Export:** A built-in history ledger tracks all URLs, queries, and answers. The *Export CSV* function saves this data using `utf-8-sig` encoding, ensuring flawless compatibility with MS Excel for Persian data.

  ### 🖋️ Premium Typography
  * **Custom Fonts Injection:** Dynamically loads Google Fonts (`Lalezar` for headings, `Baloo Bhaijaan 2` for body text) directly into the Jupyter environment for a polished, modern aesthetic.

  ---

  ## 🚀 How to Run

  1.  **Environment Setup:** Ensure you are in a Jupyter environment (JupyterLab or VS Code Notebooks).
  2.  **Install Requirements:**
      ```bash
      pip install openai chromadb sentence-transformers requests beautifulsoup4 langchain-text-splitters ipywidgets pandas markdown
      ```
  3.  **Execute Cells:** Run the cells sequentially. The system will securely prompt you for your `AVALAI_API_KEY`.
  4.  **Interact:** Once the UI panel appears in Cell 4, enter any URL, extract the data, select your language, and start asking questions!

  ---

  ## 🛠️ Tech Stack
  * **Interactive UI:** `ipywidgets`, `IPython.display` (HTML/CSS)
  * **Data Processing:** `BeautifulSoup4`, `langchain-text-splitters`
  * **Vector Database & Embeddings:** `ChromaDB`, `sentence-transformers`
  * **AI Engine:** OpenAI SDK (AvalAI Endpoint)
  * **Data Export:** `pandas`
