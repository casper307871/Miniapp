---

## Features

- Displays “Hello from your bot!” message
- Interactive button to send user info to the bot
- Fully HTTPS-ready and deployable via GitHub Pages
- Lightweight and easy to customize

---

## Usage

1. Deploy the mini app via **GitHub Pages**:
   - Push your files to a **public GitHub repository**
   - Go to **Settings → Pages** → Branch: `main` → Folder: `/ (root)` → Save
2. Copy the GitHub Pages URL (e.g., `https://yourusername.github.io/telegram-mini-app/`)
3. Use this URL in **BotFather** → `/setwebapp` for your bot
4. Open the mini app in Telegram and click **Send Info to Bot** to test

---

## Bot-side Example (Python / Pyrogram)

```python
from pyrogram import Client, filters

app = Client("my_bot")

@app.on_message(filters.command("start") & filters.private)
async def start(client, message):
    # Check if user sent Web App data
    if message.web_app_data:
        data = message.web_app_data.data
        print(f"Received Web App data: {data}")
        await message.reply_text(f"Thanks! Received your info: {data}")
    else:
        await message.reply_text("Hello! Open the mini app to send your info.")

app.run()
