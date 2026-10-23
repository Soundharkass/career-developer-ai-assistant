# CareerPilot AI

A local AI career chatbot powered by the Google Gemini API. It can explain technology concepts, explore tech careers, practice interviews, and create week-by-week learning plans with a local Python tool.

## Features

- Gemini chat using Google's `google-genai` SDK and Interactions API.
- A local `build_learning_plan` tool that Gemini can call during a conversation.
- Multi-turn chat context retained in the browser tab.
- Gemini API key stays on the Python server in `.env`; it is never sent to browser JavaScript.
- Clear diagnostic errors are shown in the chat and server terminal.

This version does not use live web search. Google Search grounding is not available on the free tier for the selected Gemini Flash model, so the bot must not claim that it checked current job listings, salaries, or news. Gemini API free-tier access and request limits depend on model and account. Check current availability and quotas in [Google AI Studio](https://aistudio.google.com/).

## Requirements

- Python 3.10 or newer
- A Gemini API key from [Google AI Studio](https://aistudio.google.com/api-keys)
- Internet access while the app is running

Google AI Studio offers free-tier access to selected Gemini models within their usage limits. The API key itself does not guarantee access to every model or unlimited usage.

## Setup on Windows PowerShell

1. Open PowerShell in this project folder.
2. Create and activate a virtual environment:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   If PowerShell blocks activation, run this in the current PowerShell window, then activate again:

   ```powershell
   Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
   .\.venv\Scripts\Activate.ps1
   ```

3. Install dependencies:

   ```powershell
   python -m pip install -r requirements.txt
   ```

4. Copy the example settings file and edit it:

   ```powershell
   Copy-Item .env.example .env
   notepad .env
   ```

   Paste your Gemini API key after `GEMINI_API_KEY=`. Keep the key private; `.env` is excluded by `.gitignore`.

5. Start the app:

   ```powershell
   python app.py
   ```

6. Open [" your locak host " link ) in your browser.

To stop the server, return to PowerShell and press **Ctrl+C**.

## Example prompts

- “I want to become a junior cybersecurity analyst. I am a beginner and can study 5 hours per week. Make me a 6-week roadmap.”
- “Explain APIs like I’m new to programming, then give me a tiny practice task.”
- “Give me one junior developer interview question at a time and coach me after each answer.”
- “Compare software testing and data analysis as entry-level careers.”

## Project structure

```text
CareerPilotAI/
├── app.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
├── templates/
│   └── index.html
└── static/
    ├── app.js
    └── styles.css
```

## Notes

- The API key is read from `GEMINI_API_KEY` (or `GOOGLE_API_KEY`) by the Python server.
- Conversation history currently lives in browser memory and clears when the page reloads.
- This is a local learning project. Add login, request limits, persistent storage, and production hosting controls before exposing it publicly.
- Free-tier usage limits and model access may change; see Google's current [Gemini API billing guide](https://ai.google.dev/gemini-api/docs/billing).
