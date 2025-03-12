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

## Example

```python
from groq import Groq
client = Groq(api_key='your_api_key')
agent = Agent(client, system="You are a helpful assistant.")
response = agent("Hello, how can you assist me?")
print(response)
```

## License
This project is for educational purposes. Use at your own discretion.
