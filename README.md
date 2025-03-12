# ReACT Agent from Scratch

This repository contains a Jupyter Notebook that demonstrates how to build a ReAct (Reasoning + Acting) agent from scratch using the `groq` API. The agent interacts with an LLM, handling user queries while maintaining a structured conversation.

## Installation

Before running the notebook, install the required dependencies:

```bash
pip install -U groq
```

## Usage

1. Open the `ReACT-agent-from-scratch.ipynb` notebook in Jupyter Notebook or JupyterLab.
2. Run the cells in sequence to initialize and interact with the agent.
3. Modify the `system` prompt in the `Agent` class to customize the behavior.

## Key Components

- **Agent Class**: Handles interactions with the `groq` API.
- **Conversation History**: Stores user and assistant messages for context.
- **Execution Function**: Calls the API and returns responses.
- **Tools**: FetchBitcoinPrice & LanguageTranslation

## Example

```python
loop(query="Tell about current bitcoin price")
loop(query="Wie hoch ist der aktuelle Bitcoin-Preis")
```
## Limitations
- **Groq API Handling**: Since Together AI isn't working due to a certification issue on my official laptop, I am using Groq for LLM interactions. My approach is flexible, allowing any LLM to be plugged in with minimal message format changes.
- **Hardcoded Language Translations**: Since Google Translate APIs are blocked in my system, I have temporarily hardcoded the translation logic. However, this can be easily integrated with any simple translation API in the future.

## License
This project is for educational purposes. Use at your own discretion.
