AI Help Desk Chatbot

Overview

The AI Help Desk Chatbot is an intelligent assistant designed to help university students with their queries regarding university policies, student guidelines, and general academic-related inquiries. It uses web scraping, document embedding, and large language models (LLMs) to provide precise answers.

How It Works 🚀

Data Collection

Scrapes university web pages using Playwright and BeautifulSoup.

Extracts text data and stores it in structured files.

Document Processing & Embeddings

Loads university guidelines, student handbooks, and scraped web data.

Splits text into smaller chunks and creates vector embeddings using sentence-transformers/all-mpnet-base-v2.

Stores embeddings in ChromaDB for efficient retrieval.

Query Processing

User asks a question via Streamlit-based UI.

Retrieves the most relevant context using semantic search on ChromaDB.

Summarizes the retrieved context using BART-Large-CNN.

Generates a final answer using LaMini-GPT-1.5B.

Features ✨

✅ Web Scraping: Extracts information from university websites dynamically.
✅ AI-Powered Answering: Uses two LLMs—BART for summarization & LaMini-GPT for response generation.
✅ ChromaDB for Retrieval: Efficiently searches for relevant content using embeddings.
✅ Fast & Scalable: Supports multiple queries and document sources.
✅ User-Friendly Interface: Built with Streamlit for easy interaction.

Why Two LLMs? 🤖🤝

We use two specialized models instead of one for optimal performance:

BART-Large-CNN: A state-of-the-art text summarization model that refines long, retrieved context into concise summaries.

LaMini-GPT-1.5B: A text-generation model fine-tuned for answering academic queries in a coherent and contextually accurate way.

Using one model for both tasks would lead to less accurate and longer responses. The two-step approach ensures better context understanding and precise answers.

Tech Stack 🛠️

Python (Primary language)

Playwright (Web Scraping)

BeautifulSoup (HTML Parsing)

LangChain (Document Processing & Retrieval)

Hugging Face Transformers (LLMs)

ChromaDB (Vector Database for retrieval)

Streamlit (Frontend for chatbot UI)

Installation Guide 🛠️

1️⃣ Clone the repository

  git clone https://github.com/your-repo/ai-help-desk-chatbot.git
  cd ai-help-desk-chatbot

2️⃣ Install Requirements

  pip install -r requirements.txt

3️⃣ Download the LLMs (Hugging Face Checkpoints)

git clone https://huggingface.co/facebook/bart-large-cnn
git clone https://huggingface.co/MBZUAI/LaMini-GPT-1.5B

⚠️ Ensure both folders (BART & LaMini-GPT) are in the project directory.

4️⃣ Run the Web Scraper (Optional)

  python scrapping.py

5️⃣ Generate Embeddings & Store in ChromaDB

  python embeddings.py

6️⃣ Start the AI Chatbot

  streamlit run main.py

Folder Structure 📂

📦 ai-help-desk-chatbot
 ┣ 📂 bart-large-cnn  # Downloaded LLM
 ┣ 📂 LaMini-GPT-1.5B  # Downloaded LLM
 ┣ 📂 chroma_db  # Vector database storage
 ┣ 📂 Data  # Scraped data and documents
 ┣ 📂 NoteBooks  # Jupyter Notebooks for preprocessing and conversions
 ┃ ┣ 📜 clean_scraping_data.ipynb  # Cleans and converts scraped text into a structured PDF
 ┃ ┣ 📜 Data_Preprocessing.ipynb  # Processes Excel student data
 ┃ ┗ 📜 CSV-to-PDF.ipynb  # Converts CSV files into formatted PDFs
 ┣ 📜 scrapping.py  # Web scraper
 ┣ 📜 embeddings.py  # Embedding generation
 ┣ 📜 utils.py  # Context retrieval, summarization, answering
 ┣ 📜 main.py  # Streamlit UI for chatbot
 ┣ 📜 requirements.txt  # Dependencies
 ┗ 📜 README.md  # Project Documentation

Jupyter Notebooks (Data Preprocessing & Conversion) 📝

The notebooks folder contains useful Jupyter notebooks for cleaning and converting data before usage in the chatbot:

1️⃣ clean_scraping_data.ipynb

Reads raw scraped text from raw_scraped_data.txt.

Cleans unwanted HTML tags, special characters, and formatting issues.

Converts the cleaned text into a structured PDF (Clean_Scrape_data.pdf).

Useful when using scrapped data for document embeddings.

How to Use:

Place your raw scraped text inside data/raw_scraped_data.txt.

Run the notebook to generate Clean_Scrape_data.pdf.

Use the cleaned PDF for embedding generation.

2️⃣ Data_Preprocessing.ipynb

Processes Excel files containing student data.

Cleans and structures the data for further analysis or AI model usage.

Useful if the chatbot requires student-specific insights.

How to Use:

Place your Excel file in the data/ folder.

Open and run Data_Preprocessing.ipynb.

The cleaned output will be available for further processing.

3️⃣ CSV-to-PDF.ipynb

Converts structured CSV data into a formatted PDF report.

Useful for generating student reports or summarizing scraped data.

How to Use:

Ensure your CSV file is inside data/.

Run CSV-to-PDF.ipynb.

The generated PDF will be available for further use.

Troubleshooting 🔧

❌ Issue: "ModuleNotFoundError: No module named 'playwright'"
✅ Fix:

pip install playwright
playwright install

❌ Issue: "Device ran out of memory (OOM Error)"
✅ Fix:

Reduce chunk_size in embeddings.py.

Use device='cpu' in models (if running on a low-GPU machine).

❌ Issue: "No response from chatbot"
✅ Fix:

Ensure both LLMs are downloaded and placed in the project directory.

Run python embeddings.py again before starting main.py.

Future Improvements 🚀

🔹 Add support for more university departments (expandable knowledge base)
🔹 Improve multi-turn conversations
🔹 Implement fine-tuned retrieval models for better accuracy
🔹 Support voice-based queries

Contributors 👨‍💻

Rehan Hanif

📧 Contact: rehan.hanif2004@gmail.com

📌 Ready to Try? Start the chatbot and explore AI-powered university assistance! 🎓🤖

