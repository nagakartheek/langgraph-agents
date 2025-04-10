# LangGraph Code-Along Playground

Welcome to the LangGraph code-along playground!  
This repository is designed for interactive sessions exploring LangGraph, LangChain, multi-agent systems, and LLM-powered workflows.

> The goal is to provide a structured, ready-to-run environment to learn, build, and experiment with LangGraph concepts — from basic nodes to advanced agent workflows.

---

## Setup

### Python Version

Ensure you're using **Python 3.11+** for full compatibility with LangGraph.

```bash
python3 --version
```

### Clone repo
```
git clone https://github.com/nagakartheek/langgraph-agents.git
$ cd langgraph-agents
```

### Create an environment and install dependencies
#### Windows Powershell
```
PS> python -m venv venv
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
PS> venv\scripts\activate
PS> pip install -r requirements.txt
```
#### Mac/Linux/WSL
```
$ python -m venv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```
After activating venv, run this command to register the virtual environment inside the jupyter kernel.
```
python -m ipykernel install --user --name=venv --display-name "Python (LG-env)"
```
* --name=myenv: the internal name of the kernel
* --display-name: how it will appear in the Jupyter UI
Then, when the Jupyter Notebook or Lab is opened, you can choose "Python (LG-env)" as the kernel for the notebook.

### Setting Up .env

1. Navigate to the `experiments/` folder:
2. Copy the example environment file to create your own `.env` file:
```
cd experiments
cp .env.example .env
```
Now, we are ready to update these values in the next stages.

### Setting Up Azure OpenAI Models

To use Azure-hosted OpenAI models, follow these steps to get your **API Key**, **Endpoint**, and **Deployment Name** configured.
If you already deployed Azure OpenAI models, directly skip to the 3rd step.

#### Step 1: Create an Azure OpenAI Resource

1. Go to the Azure Portal: [https://portal.azure.com](https://portal.azure.com)
2. Search for **"Azure OpenAI"** in the search bar.
3. Click **Create** and follow the steps:
   - Choose your subscription and resource group.
   - Set a **region** where Azure OpenAI is available (e.g., East US).
   - Give your resource a name (e.g., `my-aoai`).
   - Click **Review + Create**.

#### Step 2: Deploy a Model

1. Once your Azure OpenAI resource is created, navigate to it.
2. Go to **"Deployments"** in the left-hand menu.
3. Click **Create** or **+ Add a deployment**.
4. Choose a model (e.g., `gpt-4o` is recommended) and assign a **custom deployment name** (e.g., `gpt4-deploy`).
5. Finish and wait for the deployment to complete.

#### Step 3: Get Your API Key and Endpoint

1. In your Azure OpenAI resource, go to **"Keys and Endpoint"**.
2. Copy the **Key** (e.g., `e1fabc1234567890abcdef...`).
3. Copy the **Endpoint** (e.g., `https://my-aoai.openai.azure.com/`).

#### Step 4: Update Your `.env` File

Add the following to your `.env` file:

```env
# Azure OpenAI settings
AZURE_OPENAI_API_KEY=your-azure-openai-key
AZURE_OPENAI_ENDPOINT=https://your-resource-name.openai.azure.com/
```

### Sign up and Set LangSmith API
*  We use LangSmith for tracing and * Sign up for LangSmith [here](https://smith.langchain.com/)
*  Set `LANGCHAIN_API_KEY`, `LANGCHAIN_TRACING_V2=true`, `LANGSMITH_PROJECT`, `LANGSMITH_ENDPOINT="https://api.smith.langchain.com"` in your environment 

### Set up Tavily API for web search

* Tavily Search API is a search engine optimized for LLMs and RAG, aimed at efficient, 
quick, and persistent search results. 
* You can sign up for an API key [here](https://tavily.com/).  

* Set `TAVILY_API_KEY` in your environment.

### Environment Variables
Duplicate .env.example and rename it to .env and make sure all the environment variables are set
```env
# Azure OpenAI Configuration
AZURE_OPENAI_ENDPOINT="https://<your-azure-openai-endpoint>"
AZURE_OPENAI_API_KEY="<your_azure_openai_api_key>"

# LangSmith Configuration
LANGCHAIN_TRACING_V2=true
LANGSMITH_ENDPOINT="https://api.smith.langchain.com"
LANGSMITH_API_KEY="<your_langsmith_api_key>"
LANGSMITH_PROJECT="<your_project_id>"

# Tavily API Key
TAVILY_API_KEY="<your_tavily_api_key>"
```

### Running notebooks
Once everything is ready and setup, run the jupyter notebooks by running in the terminal.
```
$ jupyter notebook
```