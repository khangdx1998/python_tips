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

# **Logging module**
- Logging Levels

| Level  | Numberic value |
|--------|-------------|             
| CRITICAL  | 50  |
| ERROR  | 40  | 
| WARNING  | 30 |
| INFO | 20 |
| DEBUG | 10|

```python
import logging

logging.basicConfig(level = logging.DEBUG, 
                    format = "%(asctime)s-%(levelname)s-%(message)s",
                    datefmt = "%Y-%m-%d %H:%M:%S",
                    handlers=[
                        logging.FileHandler("debug.log"),
                        logging.StreamHandler()
                        ]
                    )

logging.info("Hello")                
```

# **Argparse module**
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('-n', '--name', required=True, type=int, default="", help="Name of person")

args = parser.parse_args()
print(f"Name: {args.name}")
```