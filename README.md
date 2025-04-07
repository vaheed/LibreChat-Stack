# LibreChat Stack with Ollama, RAG, Google Login, and Nginx Proxy Manager

A powerful AI chat platform built with [LibreChat](https://github.com/danny-avila/LibreChat), featuring:

✅ Local Ollama integration  
✅ RAG (Retrieval-Augmented Generation) using Qdrant  
✅ Google login support  
✅ OpenRouter integration  
✅ File and voice upload support  
✅ Database UIs (Mongo, Redis, Qdrant)  
✅ Secure public access via Nginx Proxy Manager  

---

## 📦 Features

- ✅ Local LLMs with Ollama
- ✅ OpenRouter API (Claude, GPT-4, Mistral, etc.)
- ✅ RAG with Qdrant vector DB
- ✅ Google OAuth login
- ✅ File & voice message support
- ✅ Easy Docker-based install
- ✅ Admin panel with Nginx Proxy Manager
- ✅ UI dashboards for MongoDB, Redis, and Qdrant

---

## 🚀 Installation on Ubuntu VPS

### 🖥️ Requirements

- Ubuntu 22.04+
- 2+ vCPU, 4GB+ RAM (recommended)
- Docker + Docker Compose
- Domain name (for Nginx Proxy Manager)

---

### 🛠️ 1. Install Docker & Docker Compose

```bash
sudo apt update
sudo apt install -y docker.io docker-compose
sudo usermod -aG docker $USER
newgrp docker
```

---

### 📁 2. Clone the Project

```bash
git clone https://github.com/YOUR_USERNAME/librechat-stack.git
cd librechat-stack
```

---

### 🔐 3. Configure Environment

Generate a secret:

```bash
openssl rand -base64 32
```

Open `docker-compose.yml` and update:

- `NEXTAUTH_SECRET`
- `GOOGLE_CLIENT_ID` / `GOOGLE_CLIENT_SECRET` (get from Google Cloud Console)
- `OPENROUTER_API_KEY` (optional)

---

### ☁️ 4. Start the Stack

```bash
docker compose up -d
```

---

### 🌐 5. Access Web Interfaces

🚀 Nginx Proxy Manager
Once it's up:

Go to http://your-ip:81

Login with:

Email: admin@example.com

Password: changeme

Set up proxy host like:

Domain	Forward To
```
chat.yourdomain.com	http://librechat:3080
mongo.yourdomain.com	http://mongo-express:8081
redis.yourdomain.com	http://redis-commander:8081
vector.yourdomain.com	http://qdrant-ui:3000
```

Use Nginx Proxy Manager to expose services with your own domains and apply SSL.

---

## 🤖 Using Ollama

Enter the container and pull models:

```bash
docker exec -it ollama ollama pull llama3
```

You can use any Ollama-supported models locally.

---

## 📁 Directory Structure

```
librechat-stack/
├── docker-compose.yml
├── README.md
└── (more coming soon)
```

---

## 🤝 Contributing

1. Fork the repo
2. Make your changes on a new branch
3. Submit a Pull Request

Feel free to open Issues for bugs, features, or ideas!

---

## 📄 License

MIT License © 2025 vaheeD

---

## 🙌 Credits

- [LibreChat](https://github.com/danny-avila/LibreChat)
- [Ollama](https://ollama.com)
- [Qdrant](https://qdrant.tech)
- [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager)
