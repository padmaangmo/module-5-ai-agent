# Codomax Module 5 — AI Agent, Tools & Automation

A Streamlit AI agent that uses Gemini function calling to choose and execute tools across multiple steps.

## Features
- Gemini LLM plans and chooses tools based on the user request.
- Three allowlisted tools: safe arithmetic calculator, Wikipedia lookup, and timezone-aware clock.
- Agent loop: understand task → decide tool → execute → observe → respond.
- Conversation memory in Streamlit session state, tool trace, retry logic, bounded tool rounds.
- Basic safety: no arbitrary code execution, allowlisted tools, bounded calculations, request timeouts, no key in source code.

## Run locally
```bash
pip install -r requirements.txt
streamlit run app.py
```
Create `.streamlit/secrets.toml` locally (do NOT commit):
```toml
GEMINI_API_KEY = "your_real_key"
```
For Streamlit Community Cloud, add the same setting in **App settings → Secrets**.

## Deploy
Upload the extracted files (including `app.py` and `requirements.txt`) to the root of a public GitHub repository. Deploy from Streamlit Community Cloud with main file `app.py`. Configure Secrets.

## Test questions
1. What is (250 * 18) / 100? Show the calculation.
2. Look up Retrieval-Augmented Generation on Wikipedia and summarize it with a source.
3. What is the current time in Asia/Kolkata?
4. Find a Wikipedia summary of Python, then calculate 15 * 12.
5. Remember that I am studying CSE. What am I studying? (same session)

## Limitations
- Memory is only for the current browser session, not a persistent database.
- The agent uses three predefined tools; it cannot browse arbitrary websites or send emails.
- Wikipedia is not a guaranteed source for every topic; always verify important facts.
- Google API availability, model name, and usage limits vary. Set a compatible model in the sidebar if needed.
- Tool responses are not trusted as instructions; this is an educational demonstration, not a production-secure agent.
