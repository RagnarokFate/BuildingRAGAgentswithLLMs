# Building RAG Agents with LLMs

<center>
<img src="https://dli-lms.s3.amazonaws.com/assets/general/DLI_Header_White.png" width="400" height="186" />
</center>

A comprehensive hands-on course for building **Retrieval-Augmented Generation (RAG)** agents using Large Language Models (LLMs). This project combines microservices architecture, LangChain framework, and modern AI technologies to create intelligent conversational agents.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Notebooks Guide](#notebooks-guide)
- [Microservices](#microservices)
- [Running the Application](#running-the-application)
  - [Using Docker Compose](#using-docker-compose)
  - [Running Individual Services](#running-individual-services)
- [Testing](#testing)
- [Configuration](#configuration)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## 🔍 Overview

This project provides a complete learning environment for building RAG (Retrieval-Augmented Generation) agents with Large Language Models. It demonstrates how to:

- **Build microservices-based AI applications** using Docker and FastAPI
- **Implement RAG architectures** with vector stores and embeddings
- **Create conversational AI agents** using LangChain and NVIDIA AI endpoints
- **Deploy scalable AI systems** with proper orchestration and monitoring

The course is structured as a series of Jupyter notebooks that progressively build knowledge from basic concepts to advanced implementations, culminating in a fully functional RAG chatbot system.

## ✨ Features

- **🤖 Multiple Chatbot Modes**:
  - Basic LLM access without context
  - Context-aware conversations with notebook content
  - Agentic behavior with reasoning capabilities

- **🧠 Advanced RAG Implementation**:
  - Document chunking and embedding generation
  - Vector store integration (FAISS)
  - Semantic search and retrieval

- **🌐 Microservices Architecture**:
  - Modular, scalable service design
  - Docker containerization
  - API-first approach with FastAPI

- **📚 Educational Content**:
  - Progressive learning through Jupyter notebooks
  - Hands-on exercises and examples
  - Visual aids and diagrams

## 🏗️ Architecture

The project follows a microservices architecture with the following key components:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Chatbot      │    │   LLM Client    │
│   (Gradio UI)   │◄──►│   (RAG Agent)   │◄──►│  (NVIDIA NIM)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │              ┌─────────────────┐              │
         │              │  Vector Store   │              │
         │              │    (FAISS)      │              │
         │              └─────────────────┘              │
         │                                               │
         └───────────────┐                 ┌─────────────┘
                         │                 │
                    ┌─────────────────┐    │
                    │ Docker Router   │    │
                    │  (Orchestrator) │◄───┘
                    └─────────────────┘
```

## 🚀 Getting Started

### Prerequisites

- **Docker** and **Docker Compose** installed
- **Python 3.8+** (for local development)
- **NVIDIA API Key** (for accessing NVIDIA NIM endpoints)
- **Git** for cloning the repository

### Installation

1. **Clone the repository**:
   ```powershell
   git clone <repository-url>
   cd BuildingRAGAgentswithLLMs
   ```

2. **Set up environment variables**:
   ```powershell
   # Copy the example environment file
   copy .env.example .env
   
   # Edit .env with your actual API keys
   notepad .env
   ```

   **⚠️ IMPORTANT**: Never commit your `.env` file! It's already in `.gitignore`.

3. **Build and start the services**:
   ```powershell
   cd composer
   docker-compose build
   docker-compose up -d
   ```

### Quick Start

1. **Access JupyterLab**: Navigate to `http://localhost:8888` in your browser
2. **Start with the Table of Contents**: Open `99_table_of_contents.ipynb`
3. **Follow the Learning Path**: Begin with `00_jupyterlab.ipynb` and progress through the numbered notebooks
4. **Try the Chatbot**: Access the Gradio interface at `http://localhost:8999`

## 📁 Project Structure

```
├── 📓 Notebooks (Learning Materials)
│   ├── 00_jupyterlab.ipynb          # Environment introduction
│   ├── 01_microservices.ipynb       # Microservices concepts
│   ├── 02_llms.ipynb               # Large Language Models
│   ├── 03_langchain_intro.ipynb    # LangChain framework
│   ├── 04_running_state.ipynb      # State management
│   ├── 05_documents.ipynb          # Document processing
│   ├── 06_embeddings.ipynb         # Vector embeddings
│   ├── 07_vectorstores.ipynb       # Vector databases
│   ├── 09_langserve.ipynb          # LangServe deployment
│   └── 99_table_of_contents.ipynb  # Course navigation
│
├── 🤖 Microservices
│   ├── chatbot/                    # RAG chatbot implementation
│   ├── composer/                   # Docker orchestration
│   ├── docker_router/              # Service coordination
│   ├── frontend/                   # User interface
│   └── llm_client/                 # LLM API client
│
├── 📁 Resources
│   ├── imgs/                       # Course images and diagrams
│   └── slides/                     # Presentation materials
│
└── 📄 Configuration Files
    ├── server_app.py               # Main server application
    └── requirements.txt            # Python dependencies
```

## 📚 Notebooks Guide

The course is organized as a progressive learning journey:

| Notebook | Topic | Description |
|----------|-------|-------------|
| `00` | **JupyterLab** | Environment setup and navigation |
| `01` | **Microservices** | Architecture and containerization |
| `02` | **LLMs** | Large Language Model fundamentals |
| `03` | **LangChain** | Framework introduction and usage |
| `04` | **Running State** | State management in AI applications |
| `05` | **Documents** | Document processing and chunking |
| `06` | **Embeddings** | Vector representations and similarity |
| `07` | **Vector Stores** | Database storage and retrieval |
| `09` | **LangServe** | Production deployment strategies |

## 🔧 Microservices

### Chatbot Service
- **Location**: `./chatbot/`
- **Purpose**: Core RAG agent implementation
- **Features**: Context-aware conversations, notebook integration
- **Port**: 8999 (Gradio interface)

### Frontend Service
- **Location**: `./frontend/`
- **Purpose**: User interface and assessment platform
- **Port**: 8090

### LLM Client Service
- **Location**: `./llm_client/`
- **Purpose**: API gateway to NVIDIA NIM endpoints
- **Port**: 9000

### Docker Router
- **Location**: `./docker_router/`
- **Purpose**: Service orchestration and monitoring
- **Features**: Log aggregation, health checks

## 🏃‍♂️ Running the Application

### Using Docker Compose

**Start all services**:
```powershell
cd composer
docker-compose up -d
```

**View logs**:
```powershell
docker-compose logs -f [service-name]
```

**Stop services**:
```powershell
docker-compose down
```

### Running Individual Services

**Chatbot only**:
```powershell
cd chatbot
pip install -r requirements.txt
python frontend_server.py
```

**LLM Client**:
```powershell
cd llm_client
python client_server.py
```

## 🧪 Testing

### Interactive Testing
1. **Open JupyterLab**: `http://localhost:8888`
2. **Run notebook cells**: Use `Shift+Enter` to execute cells
3. **Test chatbot**: Navigate to `http://localhost:8999`

### API Testing
```powershell
# Test LLM client endpoint
curl -X POST http://localhost:9000/v1/chat/completions -H "Content-Type: application/json" -d '{"messages": [{"role": "user", "content": "Hello!"}]}'
```

### Service Health Checks
```powershell
# Check all services status
docker-compose ps

# View service logs
docker-compose logs chatbot
```

## ⚙️ Configuration

### Environment Variables
```bash
# Required
NVIDIA_API_KEY=your_nvidia_api_key

# Optional
NVIDIA_BASE_URL=http://llm_client:9000/v1
NVIDIA_DEFAULT_MODE=open
```

### 🔒 API Key Security

For security purposes, **all hardcoded API keys have been removed** from the notebooks. When you run the notebooks, you'll be prompted to enter your API key securely using `getpass()` which hides the input.

**Two methods to set your API key:**

1. **Interactive Input** (Recommended for learning):
   ```python
   # The notebooks will prompt you with:
   # Enter your NVIDIA API Key: [hidden input]
   ```

2. **Environment File** (Recommended for development):
   ```powershell
   # Create a .env file in the project root
   echo "NVIDIA_API_KEY=your_actual_api_key_here" > .env
   ```

   Then in your notebook, load it:
   ```python
   from dotenv import load_dotenv
   load_dotenv()
   ```

**⚠️ Security Best Practices:**
- Never commit API keys to version control
- Use environment variables or secure vaults in production
- Regularly rotate your API keys
- Limit API key permissions to necessary scopes only

### Service Configuration
- **Ports**: Defined in `docker-compose.yml`
- **Dependencies**: Managed through requirements.txt files
- **Volumes**: Shared storage for notebook content and assessments

## 🌐 API Endpoints

### Chatbot Service (Port 8999)
- **GET** `/` - Gradio interface
- **POST** `/chat` - Chat completion endpoint

### LLM Client (Port 9000)
- **POST** `/v1/chat/completions` - OpenAI-compatible endpoint
- **GET** `/health` - Health check

### Frontend (Port 8090)
- **GET** `/` - Assessment interface
- **POST** `/submit` - Assessment submission

## 🤝 Contributing

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes** and test thoroughly
4. **Commit your changes**: `git commit -m 'Add amazing feature'`
5. **Push to the branch**: `git push origin feature/amazing-feature`
6. **Open a Pull Request**

## 🔧 Troubleshooting

### Common Issues

**Services won't start**:
- Check Docker is running: `docker --version`
- Verify ports aren't in use: `netstat -an | findstr :8999`
- Check logs: `docker-compose logs`

**Notebook cells fail**:
- Ensure all services are running
- Check network connectivity between containers
- Verify API keys are set correctly

**API Key Issues**:
- Ensure your NVIDIA API key is valid and active
- Check that the key starts with 'nvapi-'
- Verify your API key hasn't expired
- Make sure you have sufficient API quota/credits

**Permission errors**:
- On Windows, ensure Docker has proper permissions
- Check file sharing settings in Docker Desktop

**Memory issues**:
- Increase Docker memory allocation
- Monitor resource usage: `docker stats`

### Getting Help

1. **Check logs**: `docker-compose logs [service-name]`
2. **Restart services**: `docker-compose restart`
3. **Rebuild containers**: `docker-compose build --no-cache`
4. **Review documentation** in the notebooks

## 📄 License

This project is part of NVIDIA's Deep Learning Institute curriculum. Please refer to NVIDIA DLI terms and conditions for usage rights and restrictions.

---

**🎯 Ready to build your first RAG agent?** Start with the [Table of Contents](99_table_of_contents.ipynb) and begin your journey into the world of AI-powered conversational agents!
