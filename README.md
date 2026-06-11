# 🛒 AI Shopping Assistant

An intelligent shopping agent powered by **Groq** and **LangChain** that lets you search for products by text or image, check ratings, and place orders — all through a natural conversational interface.

---

## ✨ Features

- 🔍 **Smart Product Search** — Describe what you want in plain English (e.g. *"organic honey under $15 with 4+ rating"*) and the agent finds the best matches
- 🖼️ **Image-Based Search** — Upload a photo of any product and the agent visually analyzes it to find similar items in the store
- ⭐ **Live Ratings** — Every search result includes the average customer rating and review count
- 🛍️ **One-Click Ordering** — Confirm your choice in chat and the agent places the order instantly
- 💬 **Conversational UI** — Natural back-and-forth chat so you can refine your search, set filters, or ask follow-up questions

---

## 🧠 How It Works

The app uses a **LangChain agent** backed by **Groq's LLaMA 3** model that autonomously decides which tools to call:

| Tool | What it does |
|---|---|
| `search_products` | Queries a local SQLite database by keyword, price, and organic status |
| `get_rating` | Fetches average rating and review count for a product |
| `checkout` | Places an order and saves it to the database |
| `describe_product_image` | Uses Llama 4 Scout vision model to analyze an uploaded image and extract search attributes |

---

## 🖥️ Demo

> **Text search:** *"I want organic honey under $20 with at least 4.5 stars"*
>
> **Image search:** Upload a photo of olive oil → agent identifies it → finds matching products → shows prices and ratings

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- A free [Groq API key](https://console.groq.com/keys)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Sjkewat/shopping-agent.git
cd shopping-agent

# 2. Create and activate a virtual environment
python -m venv .venv
.venv\Scripts\activate       # Windows
source .venv/bin/activate    # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set up your environment variables
```

Create a `.env` file in the `4_shopping_agent/` folder:
```env
GROQ_API_KEY=your_groq_api_key_here
```

### Run the App

```bash
streamlit run 4_shopping_agent/app.py
```

The app will open at `http://localhost:8501`

---

## 📁 Project Structure

```
4_shopping_agent/
├── app.py               # Streamlit UI — chat interface and image upload sidebar
├── shopping_agent.py    # LangChain agent — tools, LLM setup, system prompt
├── reviews_api.py       # Reviews API — fetches product ratings
├── store.db             # SQLite database — products and orders
└── .env                 # API keys (not committed to git)
```

---

## 🌐 Deployment (Streamlit Cloud)

1. Push the repo to GitHub
2. Go to [share.streamlit.io](https://share.streamlit.io) and connect your repo
3. Set the main file path to `4_shopping_agent/app.py`
4. Add your secret under **Settings → Secrets**:
```toml
GROQ_API_KEY = "your_groq_api_key_here"
```
5. Click **Deploy** — your app gets a live public URL!

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=for-the-badge&logo=groq&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

- **Frontend:** Streamlit
- **Agent Framework:** LangChain + LangGraph
- **LLM:** Groq `llama3-8b-8192` (text) + `meta-llama/llama-4-scout-17b-16e-instruct` (vision)
- **Database:** SQLite
- **Deployment:** Streamlit Cloud

---

## 📝 Example Queries

```
"Show me organic olive oil under $10"
"Find almonds with a rating above 4 stars"
"I want something sweet and non-organic under $5"
"Order the first one"
"Yes, go ahead"
```

Or just upload a product photo and let the agent figure it out!

---

## 🔒 Environment Variables

| Variable | Description |
|---|---|
| `GROQ_API_KEY` | Your Groq API key from [console.groq.com](https://console.groq.com/keys) |

---

## 👤 Author

**Arav** — [@Sjkewat](https://github.com/Sjkewat)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
