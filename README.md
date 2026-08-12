# LangChain Multi-Agent Research System

A learning-focused multi-agent research app built with Python, LangChain, and OpenAI. The system searches for relevant information, scrapes the most useful sources, writes a detailed research report, and then reviews the report with a critic agent.

## Project Overview

This project demonstrates a simple multi-agent workflow:

1. Search Agent: Finds relevant and recent information on a topic.
2. Reader Agent: Chooses a useful source and scrapes the page content.
3. Writer Chain: Turns the gathered research into a structured report.
4. Critic Chain: Reviews the report and gives feedback.

The app includes a Streamlit interface for interacting with the workflow locally.

## Architecture

```text
User Input
   |
   v
Streamlit UI (app.py)
   |
   v
Research Pipeline (src/pipelines/pipeline.py)
   |
   +--> Search Agent (src/agents/agents.py)
   |      Uses Tavily web search
   |
   +--> Reader Agent (src/agents/agents.py)
   |      Uses URL scraping tools
   |
   +--> Writer Chain
   |      Uses ChatPromptTemplate + LLM + StrOutputParser
   |
   +--> Critic Chain
          Uses ChatPromptTemplate + LLM + StrOutputParser
```

### Main modules

- `app.py`: Streamlit frontend for the app
- `main.py`: quick local script entry point
- `src/agents/agents.py`: agent and LLM chain definitions
- `src/tools/tools.py`: search and scraping tools
- `src/pipelines/pipeline.py`: orchestration logic for the research flow
- `requirements.txt`: project dependencies

## Tech Stack

- Python 3.10+
- LangChain
- LangChain OpenAI
- OpenAI GPT models
- Streamlit
- Tavily API
- BeautifulSoup
- readability-lxml
- trafilatura
- python-dotenv
- Requests

## Prerequisites

Before running the project, make sure you have:

- Python installed
- An OpenAI API key
- A Tavily API key

## Local Setup

### 1. Clone the project

```bash
git clone <your-repo-url>
cd Langchain-Multi-Agent-research-system
```

### 2. Create a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Create a .env file

Create a file named `.env` in the project root with the following values:

```env
OPENAI_API_KEY="your_openai_api_key_here"
TAVILY_API_KEY="your_tavily_api_key_here"
```

## How to Run

### Option 1: Run Streamlit app

```bash
streamlit run app.py
```

This starts the interactive research assistant in your browser.

### Option 2: Run the pipeline script directly

```bash
python main.py
```

This is useful for quick testing of the research workflow in the terminal.

## Example Usage

After starting the app, enter a topic such as:

```text
Latest AI trends in healthcare
```

The system will:

- search for relevant web sources,
- extract content from the best source,
- generate a detailed report,
- and provide a critic review.

## Notes

- The app depends on valid API keys stored in `.env`.
- The scraping step may behave differently depending on the website structure and anti-bot protections.
- This project is intended for learning and experimentation with multi-agent AI workflows.

## License

This project is licensed under the MIT License. See `LICENSE` for more details.