# Telegram Bot
This Python project is a simple implementation of a Telegram bot that can send messages and photos to users. The bot uses the Telegram Bot API to communicate with users and handle incoming messages.

## Features
- Fetch updates from the bot's server
- Send text messages to users
- Send photos to users

## Dependencies
- requests: A library for making HTTP requests in Python

## Installation
1. Clone this repository:

```git clone https://github.com/your-username/telegram-bot.git```

2. Install the required dependencies:

```pip install -r requirements.txt```

3. Create a new bot on Telegram by talking to the BotFather and obtain your bot token.
4. Set environment variables for your bot:

```
export TELEGRAM_BOT_NAME="your_bot_name"
export TELEGRAM_BOT_TOKEN="your_bot_token"
```

## Usage
1. Import the TelegramBot class:

```from telegram_bot import TelegramBot```

2. Create an instance of the TelegramBot class:

```bot = TelegramBot()```

3. Use the get_updates() method to fetch updates from the bot's server:

```updates = bot.get_updates()```

4. Send a text message to a user:

```chat_id = 123456789
text = "Hello, World!"
bot.send_message(chat_id, text)```

5. Send a photo to a user:

```chat_id = 123456789
with open("path/to/your/image.jpg", "rb") as image:
    bot.send_photo(chat_id, image)```

6. Download a voice file

To use the **download_voice_file** method, you first need to obtain the **file_id** of the voice message. You can get the file_id from an update received by your bot when someone sends a voice message. Here's an example of how to use the download_voice_file method:

    ```from telegram_bot import TelegramBot

    bot = TelegramBot()

    # Get updates from the bot's server
    updates = bot.get_updates()

    # Iterate through the updates to find a voice message
    for update in updates['result']:
        if 'voice' in update['message']:
            # Get the file_id of the voice message
            file_id = update['message']['voice']['file_id']
            
            # Download the voice file using the file_id
            voice_data = bot.download_voice_file(file_id)
            
            # Save the voice file to the local storage
            with open("voice_message.ogg", "wb") as voice_file:
                voice_file.write(voice_data.read())
            
            print("Voice message saved as 'voice_message.ogg'")
            break```
