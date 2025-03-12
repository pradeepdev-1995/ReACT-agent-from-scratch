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
## Approach for Prompting

This system operates in a structured loop consisting of four key phases: **Thought, Action, PAUSE, and Observation**, before finally producing an **Answer**.

### 1. Understanding the Question (Thought Phase)
- The system first **analyzes the query** to determine the necessary action.  
- If the query is **not in English**, it requires **language translation** before proceeding.  
- If the query is in **English** and directly asks for Bitcoin’s price, the system proceeds to **fetch the latest price**.  

### 2. Taking Action (Action Phase)
- Based on the thought process, the system **invokes the appropriate action**:  
  - **FetchBitcoinPrice** → Fetches the latest BTCUSDT price.  
  - **LanguageTranslation** → Converts a non-English query into English.  
- The system then **pauses (PAUSE)** and waits for the action’s result.  

### 3. Receiving Results (Observation Phase)
- The system receives the **result of the action taken** (e.g., translated query or Bitcoin price).  
- If necessary, the system continues the loop by **executing another action** (e.g., fetching the Bitcoin price after translation).  

### 4. Generating the Answer (Final Output)
- Once the required data is obtained, the system **formats and returns the final answer**.  
- The response follows a structured pattern:  
  - **Example 1:** `"The current bitcoin price is 6234925."`  
  - **Example 2:** `"The current bitcoin price is 8934712."`  

## Example

### Example 1
```python
Input:
loop(query="tell about current bitcoin price ")
Output:
Thought: I should look up FetchBitcoinPrice Function
Action: FetchBitcoinPrice: BTCUSDT
PAUSE
next_prompt IS
Observation: 81948.48
Thought: I think I have found the answer
Action: 81948.48
Answer: The current bitcoin price is 81948.48
```
### Example 2
```python
Input:
loop(query="Wie hoch ist der aktuelle Bitcoin-Preis")
Output:
Thought: This is not English language, so I need to translate first this to english

Action: LanguageTranslation : "Wie hoch ist der aktuelle Bitcoin-Preis?"
PAUSE
next_prompt IS
Observation: What is the current price of Bitcoin?
Thought: Now I got the original query in english language, Now I should look up FetchBitcoinPrice Function

Action: FetchBitcoinPrice : BTCUSDT
PAUSE
next_prompt IS
Observation: 81956.3
Thought: I think I have found the answer
Action: 81956.3

Answer: The current price of Bitcoin is 81956.3
```

## Limitations
- **Groq API Handling**: Since Together AI isn't working due to a certification issue on my official laptop, I am using Groq for LLM interactions. My approach is flexible, allowing any LLM to be plugged in with minimal message format changes.
- **Hardcoded Language Translations**: Since Google Translate APIs are blocked in my system, I have temporarily hardcoded the translation logic. However, this can be easily integrated with any simple translation API in the future.

## License
This project is for educational purposes. Use at your own discretion.
