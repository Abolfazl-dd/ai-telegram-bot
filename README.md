# 🤖 AI Telegram Assistant

A Python Telegram bot that combines **Gemini AI** with a simple **JSON-based note system**.

The bot allows users to chat with Gemini, save personal notes, view notes, delete notes, and ask Gemini to summarize a specific note.

## ✨ Features

* 🤖 Chat with Gemini AI
* 📝 Add personal notes
* 📋 View saved notes
* 🗑️ Delete notes
* ✨ Summarize notes using Gemini
* 👤 Separate notes for each Telegram user
* 🔐 API keys stored using environment variables
* 💾 Notes stored locally in a JSON file

## 🛠️ Technologies

* Python
* `python-telegram-bot`
* Google Gemini API
* `google-genai`
* `python-dotenv`
* JSON

## 📂 Project Structure

```text
ai-telegram-assistant/
│
├── bot.py
├── note.json
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

> `.env` should not be uploaded to GitHub because it contains secret API keys.

## 🚀 Installation

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
cd ai-telegram-assistant
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## 🔑 Environment Variables

Create a `.env` file:

```env
BOT_TOKEN=your_telegram_bot_token
GEMINI_API_KEY=your_gemini_api_key
```

The application loads these values with `python-dotenv`.

## ▶️ Run the Bot

```bash
python bot.py
```

You should see:

```text
Bot is running...
```

Then open your Telegram bot and use the commands below.

## 📱 Commands

| Command                 | Description                             |
| ----------------------- | --------------------------------------- |
| `/start`                | Start the bot                           |
| `/help`                 | Show available commands                 |
| `/chat <message>`       | Ask Gemini a question                   |
| `/add_note <text>`      | Save a note                             |
| `/show_notes`           | Show your notes                         |
| `/delete_note <number>` | Delete a note                           |
| `/summarize <number>`   | Summarize one of your notes with Gemini |

### Example

```text
/add_note Python is useful for AI and automation
```

Then:

```text
/show_notes
```

You may see:

```text
1_ Python is useful for AI and automation
```

Then:

```text
/summarize 1
```

The bot sends the original note together with an AI-generated summary.

## 🧠 How It Works

### AI Chat

```text
Telegram User
      ↓
/chat <message>
      ↓
Python Bot
      ↓
Gemini API
      ↓
AI Response
      ↓
Telegram User
```

### Note Summarization

```text
Telegram User
      ↓
/summarize 1
      ↓
Load note from note.json
      ↓
Send note to Gemini
      ↓
Generate summary
      ↓
Send summary to Telegram
```

## 💾 Data Storage

Notes are stored in `note.json`.

The bot uses the Telegram user's ID as the key, so different users have separate note lists.

Example:

```json
{
    "123456789": [
        "Learn Python",
        "Build an AI Telegram bot"
    ],
    "987654321": [
        "Learn APIs"
    ]
}
```

## 🔐 Security

API keys are loaded from environment variables:

```python
BOT_TOKEN = os.getenv("BOT_TOKEN")
GEMINI_API_KEY = os.getenv("GEMINI_API_KEY")
```

Do not commit `.env` to GitHub.

Example `.gitignore`:

```text
.env
__pycache__/
.venv/
```

## ☁️ Deployment

The bot can be deployed to a cloud platform that supports long-running Python services.

For deployment, configure these environment variables on the server:

```text
BOT_TOKEN
GEMINI_API_KEY
```

Example start command:

```bash
python bot.py
```

## 🔮 Future Improvements

* Add Gemini error handling
* Add conversation memory
* Improve note display formatting
* Replace JSON storage with a database
* Add inline keyboard buttons
* Add user settings
* Add better logging
* Improve production deployment

## 🎯 Project Goal

This project was built as part of my Python and freelancing learning path to practice:

* Python
* Telegram Bot development
* REST/API usage
* JSON data storage
* Environment variables
* AI integration
* Deployment

## 📄 License

This project is for learning and portfolio purposes.
