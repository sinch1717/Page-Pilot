# 🚀 PagePilot – Automated Static Website Generator

**PagePilot** is a FastAPI-based automation service that generates, deploys, and hosts static websites using large language models (LLMs) like GPT or Claude.  
It automates the entire process — from receiving a website brief to deploying the final site on GitHub Pages.

---

## 🎯 Overview

PagePilot is an **AI-powered website generator** that:
- Takes a text-based project brief as input
- Uses an LLM (GPT/Claude) to generate a complete static site
- Creates a new GitHub repository
- Pushes generated files automatically
- Publishes the site using **GitHub Pages**

It’s designed to showcase automation, API design, and LLM integration using **FastAPI**, **LangChain**, and the **GitHub API**.

---

## ⚙️ Features

- **Single API Endpoint** – Accepts website generation requests  
- **Secure Authentication** – Uses secret key validation  
- **Asynchronous Processing** – Handles long-running tasks in the background  
- **LLM Integration** – Works with OpenAI (GPT) or Anthropic (Claude)  
- **GitHub Automation** – Creates repositories, pushes code, and enables GitHub Pages  
- **Error Handling & Retry Logic** – Ensures reliability for deployment and generation  
- **Health Check Endpoints** – For monitoring and configuration verification  

---

## 🧩 Tech Stack

- **Backend Framework:** FastAPI  
- **AI Integration:** LangChain (OpenAI / Anthropic)  
- **Version Control:** GitHub API (via PyGithub)  
- **Deployment:** GitHub Pages / Vercel  
- **Language:** Python 3.10+  

---

## 🛠️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/pagepilot.git
cd pagepilot
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables
Create a `.env` file (copy from `.env.example`):

```bash
cp .env.example .env
```

Edit and fill in the following:
```
SECRET_KEY=your-secret-key
GITHUB_TOKEN=your-github-token
LLM_PROVIDER=openai
OPENAI_API_KEY=your-openai-api-key
ANTHROPIC_API_KEY=your-anthropic-api-key
```

> **Note:**  
> - `GITHUB_TOKEN` requires scopes: `repo`, `admin:repo_hook`  
> - Use either `OPENAI_API_KEY` or `ANTHROPIC_API_KEY` depending on the LLM provider.  

---

### 4. Run the Server Locally
```bash
uvicorn app:app --reload
```

Visit the app at:
```
http://localhost:8000
```

---

## 🧪 Testing the API

You can test the API locally using Python or curl.

### Example Request
```bash
curl -X POST http://localhost:8000/api-endpoint   -H "Content-Type: application/json"   -d '{
    "email": "test@example.com",
    "secret": "your-secret-key",
    "task": "portfolio-site",
    "brief": "Create a modern portfolio website with a hero section and contact form."
  }'
```

**Response:**
```json
{
  "status": "ok"
}
```

The app will then generate the site, create a GitHub repository, and publish it automatically.

---

## 🌐 Deploying to Vercel

### 1. Install Vercel CLI
```bash
npm i -g vercel
```

### 2. Deploy
```bash
vercel
```

### 3. Add Environment Variables
Use the Vercel dashboard or CLI:
```bash
vercel env add SECRET_KEY
vercel env add GITHUB_TOKEN
vercel env add LLM_PROVIDER
vercel env add OPENAI_API_KEY
vercel env add ANTHROPIC_API_KEY
```

> For production environments, consider **Railway**, **Render**, or **AWS Lambda** for longer-running tasks.

---

## 🔄 Switching Between LLM Providers

You can switch models anytime by updating your `.env`:

### Use OpenAI (GPT)
```bash
LLM_PROVIDER=openai
OPENAI_API_KEY=your-key
```

### Use Anthropic (Claude)
```bash
LLM_PROVIDER=anthropic
ANTHROPIC_API_KEY=your-key
```

---

## 📁 Project Structure
```
pagepilot/
├── app.py                  # FastAPI main app
├── github_service.py       # Handles GitHub repo automation
├── llm_service.py          # LLM (GPT/Claude) integration via LangChain
├── evaluation_service.py   # Handles status reporting and retries
├── test_api.py             # Local API testing script
├── requirements.txt        # Project dependencies
├── .env.example            # Environment variable template
├── vercel.json             # Deployment configuration
└── README.md               # Project documentation
```

---

## 🔐 Security Best Practices

- Never commit `.env` or any secrets to version control  
- Rotate API keys and GitHub tokens periodically  
- Use environment variables for sensitive data  
- Review permissions before granting token scopes  

### Checking for Leaked Secrets
Use [**gitleaks**](https://github.com/gitleaks/gitleaks) to scan your repo:
```bash
gitleaks detect --source . --verbose
```

---

## 🩺 Troubleshooting

| Issue | Possible Fix |
|-------|---------------|
| `SECRET_KEY not configured` | Ensure `.env` file exists and has `SECRET_KEY` |
| `GITHUB_TOKEN not set` | Add a valid GitHub token with `repo` access |
| `OPENAI_API_KEY not set` | Add a valid OpenAI API key |
| LLM not generating valid HTML | Check server logs or switch LLM provider |
| GitHub Pages not enabling | Enable manually via repo → Settings → Pages |

---

## 💡 Example Workflow

1. You send a website generation request via the API  
2. PagePilot validates the secret and starts background processing  
3. The LLM generates HTML/CSS/JS files for the project  
4. A GitHub repository is created and populated  
5. GitHub Pages is enabled automatically  
6. Your generated website goes live in seconds 🎉  

---

## ✅ Pre-Deployment Checklist

- [ ] Dependencies installed (`pip install -r requirements.txt`)  
- [ ] `.env` configured with all API keys  
- [ ] Server starts at `http://localhost:8000`  
- [ ] API returns `{"status": "ok"}`  
- [ ] GitHub repo and Pages deploy successfully  

---

## 📚 References

- [FastAPI Documentation](https://fastapi.tiangolo.com/)  
- [LangChain Docs](https://python.langchain.com/)  
- [PyGithub Docs](https://pygithub.readthedocs.io/)  
- [GitHub Pages Guide](https://docs.github.com/en/pages)  

---

## 🤝 Contributing

Pull requests and feature suggestions are welcome!  
For major changes, please open an issue first to discuss what you’d like to improve.

---

## 🧠 About the Project

PagePilot was built as a personal experiment in **automation, LLM integration, and API orchestration**.  
It demonstrates how AI can autonomously design, build, and deploy complete websites with minimal human intervention.

---

**Built with ❤️ using FastAPI, LangChain, and the GitHub API.**
