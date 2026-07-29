# 💰 **FinBot** — Financial Literacy RAG Chatbot

> A trustworthy financial education chatbot powered by Retrieval-Augmented Generation (RAG) that provides accurate, source-cited answers about personal finance.

## 🎯 Features

- ✅ **Accurate Financial Education:** Answers from verified sources (CFPB, Investopedia, Investor.gov)
- ✅ **Source Transparency:** Every answer cites its sources with similarity scores
- ✅ **Hallucination Prevention:** Refuses questions outside knowledge base scope
- ✅ **No Personalized Advice:** Educational guidance without crossing ethical boundaries
- ✅ **Fast Response Time:** Sub-2-second latency with Groq LLM inference

## 🏗️ Architecture

### **Phase 1: Data Curation**
- Scraped 47 documents from 3 authoritative sources
- Created 1,101 text chunks (600 chars, 120 char overlap)
- Topics: retirement planning, credit, investing, mortgages, taxes, insurance

### **Phase 2: Indexing**
- Embeddings: `sentence-transformers/all-MiniLM-L6-v2` (384-dim)
- Vector database: FAISS with flat index for exact search
- Semantic similarity: Cosine similarity with 0.5 threshold

### **Phase 3: RAG Pipeline**
- LLM: Groq (`llama-3.1-8b-instant`) for fast, free inference
- Context-aware prompting with strict grounding instructions
- Performance: 0.3–1.5s generation time

### **Phase 4: Interface**
- Streamlit web UI with chat interface
- Source display panel for transparency
- Example questions and knowledge base statistics

git clone https://github.com/tom32bit/FinBot-RAG-Chatbot.git
pip install -r requirements.txt
## 🚀 Quick Start

### **Prerequisites**
- Python 3.8+
- Groq API key ([get free key](https://console.groq.com/))

### **Installation**

1. **Clone the repository**
	```sh
	git clone https://github.com/tom32bit/FinBot-RAG-Chatbot.git
	cd finbot-rag-chatbot
	```

2. **Install dependencies**
	```sh
	pip install -r requirements.txt
	```

3. **Set up environment variables**
	- Create a `.env` file in the project root:
	  ```env
	  GROQ_API_KEY=your_groq_api_key_here
	  ```

4. **Run data curation (Phase 1)**
	```sh
	python phase1_data_curation.py
	```

5. **Build vector index (Phase 2)**
	```sh
	python phase2_indexing.py
	```

6. **Launch the chatbot**
	```sh
	python -m streamlit run phase4a_streamlit_ui.py
	```

The app will open at [http://localhost:8501](http://localhost:8501)

## 📊 Evaluation Results

### **Safety Testing** (7/7 Pass Rate)
- ✅ Out-of-domain refusal (cryptocurrency, quantum computing)
- ✅ Inappropriate questions (credit score hacking)
- ✅ Product recommendations (specific credit cards)
- ✅ Market timing questions (house buying advice)
- ✅ Educational vs personalized advice boundary

### **Performance Metrics**
- **Total Chunks:** 1,101
- **Documents:** 47
- **Average Retrieval Time:** 3–25ms
- **Average Generation Time:** 300–1,500ms
- **Retrieval Precision:** 85%+ (chunks above 0.5 threshold)

## 🎓 Example Questions

### ✅ In-Domain (Answered)
- What is a 401k retirement plan?
- How does credit score work?
- What's the difference between stocks and bonds?
- How does compound interest work?

### ❌ Out-of-Domain (Refused)
- What's the best cryptocurrency to buy?
- Should I invest in Tesla stock?
- How to hack my credit score?

## 📁 Project Structure

```
finbot-rag-chatbot/
├── phase1_data_curation.py      # Web scraping & chunking
├── phase2_indexing.py           # Embedding generation & FAISS indexing
├── phase3_rag_pipeline.py       # RAG pipeline with Groq LLM
├── phase4a_streamlit_ui.py      # Web interface
├── requirements.txt             # Python dependencies
├── .env.example                 # Environment variables template
├── .gitignore                   # Git ignore rules
└── README.md                    # This file
```

## 🔒 Security & Ethics

- **No Personalized Advice:** Provides educational information only
- **Source Attribution:** All answers cite original sources
- **Scope Limitation:** Refuses questions outside knowledge base
- **Privacy:** No user data collection or storage

## 🛠️ Technologies Used

- **Frontend:** Streamlit
- **Embeddings:** Sentence Transformers (`all-MiniLM-L6-v2`)
- **Vector Database:** FAISS
- **LLM:** Groq (`llama-3.1-8b-instant`)
- **Web Scraping:** BeautifulSoup4, Requests

## 📝 License

MIT License — See LICENSE file for details

## 🤝 Contributing

Contributions welcome! Please open an issue or submit a pull request.

## 👨‍💻 Author

**Team:** ACRS_BRAC

## 🏆 Hackathon Project

Built for **[SOLVIO AI HACKATHON]** — November 2025
