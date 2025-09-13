# Automated-Security-Prototype
ESP32 + PIR + Telegram Bot
(No schetch)

Video: [click here](https://drive.google.com/file/d/1Zyd9LXnaxaLlG2VcHzpNk53Nki-j1hdI/view?usp=sharing)

This is my first experience of creating an automated security system.
The idea was to use ESP32 as a microcontroller, PIR motion sensor for presence detection and Telegram bot for sending alarm notifications.
Also added buzzer for local signal.
The project was conceived as a simple system for a home/room, which can be developed into a full-fledged security system.

Components:

ESP32 (NodeMCU-32S)
PIR motion sensor (HC-SR501) - don't buy this one I played it safe and took the one with 3.3 V output 
but it's really bad and I also got a defective one so the sensor was constantly hanging in High mode regardless of the position of the jumper and trimmer resistors
Buzzer
Wi-Fi connection
Telegram Bot API


How it was supposed to work:

1.PIR sensor detects movement.
2.ESP32 receives signal and turns on buzzer.
3.ESP32 sends notification to Telegram via bot.
4.User sees message in chat and can react.
(very simple, right?)

Connecting bot to esp 32:

1.Connecting to Wi-Fi
The ESP32 code specifies the network name (SSID) and password (PASSWORD).
After uploading the sketch, the ESP32 connects to the router and receives a local IP.

2.Creating a Telegram bot
In the Telegram application, find the bot @BotFather.
Use the /newbot command to create a new bot.
BotFather will give you an API Token (a string like 123456789:ABC-DEF...).
This token is saved in the ESP32 code.

Getting a Chat ID
Find the bot @userinfobot or @RawDataBot.
Click Start — it will give you your chat_id.
This chat_id is also saved in the code so that the bot knows where to send notifications.

3.Sending messages
The ESP32 uses an HTTP request to the Telegram API
