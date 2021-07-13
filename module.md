# **Telegram notification with Python**
- Install telegram module: **pip install python-telegram-bot**
```python
import telegram

#Define API_TOKEN and ID_CHAT
API_TOKEN="xxxxxx"
ID_CHAT="xxxxxx"

bot = telegram.Bot(token=API_TOKEN)
bot.sendMessage(chat_id=ID_CHAT, text=message)
```