# 🤖 Local AI Chat & Finance Hub

![Python Version](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-brightgreen.svg)
![Ollama](https://img.shields.io/badge/Ollama-Local%20LLM-orange.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

A private, 100% local AI assistant built with Streamlit and Ollama. This app features an OCR-powered bank statement parser, a "Chat with your Docs" RAG system, and a complete personal finance tracker.

![Project Demo Screenshot](image_83e1da.png)
*(Note: You will need to add your `image_83e1da.png` file to the root of your repository for this image to display)*

---

## 🚀 Core Features

This application combines two powerful AI systems into a single, easy-to-use interface.

### 1. 💰 AI-Powered Finance Tracker
A complete personal finance dashboard that understands your documents.

* **AI Statement Parsing:** Automatically extract all transactions by uploading **PDF** or **CSV** bank statements.
* **Advanced OCR:** Uses Tesseract and OpenCV to accurately read **scanned, image-based PDFs**—not just digitally generated ones.
* **Full Transaction Management:** Manually add, edit, and delete expenses and earnings.
* **Data Visualization:** A multi-tab dashboard to visualize your finances:
    * **Overview:** See your current daily, weekly, and monthly net cash flow.
    * **Analytics:** View charts for Earnings vs. Expenses, category spending, and all-time financial stats.
    * **History:** A full, filterable log of all past transactions.
    * **Calendar View:** Click on any date to see all transactions for that specific day.

### 2. 📚 RAG (Retrieval-Augmented Generation) Chatbot
A general-purpose chatbot with long-term memory for your personal knowledge base.

* **Chat with your Data:** Upload your own PDFs and images (PNG, JPG) to the chat.
* **Vector Database:** Uses **ChromaDB** to create a local vector store, allowing you to ask questions and get context-aware answers based *only* on your uploaded files.
* **Smart Suggestions:** Automatically generates relevant follow-up questions for any document you upload.
* **Persistent Chat:** Saves and loads all your chat sessions, so you never lose your history.

---

## 🛠️ Tech Stack & How It Works

This project runs 100% locally on your machine. Your data never leaves your computer.

* **Frontend:** Streamlit
* **Local LLM:** Ollama (using `gemma3:4b` for reasoning and parsing)
* **Embedding Model:** Ollama (using `nomic-embed-text`)
* **OCR Engine:** Tesseract-OCR & Poppler
* **Image Processing:** OpenCV
* **Vector DB:** ChromaDB
* **Orchestration:** Langchain & Agno

---

## ⚙️ Setup and Installation

This project has three main setup stages. **Please follow them in order.**

### Part 1: Install System Dependencies

These tools are **required** for the OCR and PDF processing to function.

1.  **Ollama:**
    * Download and install Ollama from [ollama.com](https://ollama.com/).
    * Ensure the Ollama application is **running in the background** before starting the app.

2.  **Tesseract-OCR (For reading text from images):**
    * Download the Windows installer from: [https://github.com/UB-Mannheim/tesseract/wiki](https://github.com/UB-Mannheim/tesseract/wiki)
    * When running the installer, **you must check the box** to "Add Tesseract to system PATH."

3.  **Poppler (For converting PDF pages to images):**
    * Poppler does not have an installer. Download the latest Windows binary zip file from [here](https://github.com/oschwartz10612/poppler-windows/releases/).
    * Unzip this file to a **permanent** location (e.g., `C:\Program Files\poppler`).
    * You must **manually** add its `bin` folder to your system `PATH`:
        1.  Search for "Edit the system environment variables" in the Start Menu.
        2.  Click "Environment Variables..."
        3.  Under "System variables," find and select `Path`, then click "Edit..."
        4.  Click "New" and paste the full path to the `bin` folder (e.g., `C:\Program Files\poppler\bin`).
        5.  Click OK on all windows to save.

**IMPORTANT:** You **must restart your computer** (or at least your terminal and code editor) after installing these and updating your `PATH`.

#### Verify Installation (Optional but Recommended)
Open a **new** terminal and run these commands. If they show a version number, you are set.
```bash
tesseract --version
pdftoppm -v 
```




Part 2: Setup Python Project
1.Clone the repository:
```Bash
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name
```

2.Create a virtual environment:
```Bash
python -m venv venv
venv\Scripts\activate
```
3.Install Python packages: Create a file named requirements.txt in your project folder, paste the content below into it, and save it.
requirements.txt:
```
streamlit
plotly
pandas
pytesseract
pdf2image
opencv-python-headless
agno
langchain-ollama
langchain-community
langchain-text-splitters
langchain-core
chromadb
```
Now, run the installation from your terminal:
```Bash
pip install -r requirements.txt
```
Part 3: Download AI Models
Open your terminal and pull the required models from Ollama:

# Pull the embedding model (for vectorizing text)
```Bash
ollama pull nomic-embed-text
```
# Pull the main AI model (for chat, RAG, and parsing)
```Bash
ollama pull gemma3:4b
ollama pull gemma3:1b
```
▶️ How to Run
1)Ensure your Ollama application is running.

2)Activate your virtual environment (if it's not already):
```Bash
venv\Scripts\activate
```
3)Run the Streamlit app:
```Bash
streamlit run your_script_name.py
```
4)Open the local URL (e.g., http://localhost:8501) in your browser.
