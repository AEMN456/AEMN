import telebot
from telebot import types

bot = telebot.TeleBot("5943018739:AAGZ1nWbjUdGThbkHCumm-friZIQ7qQyj8M")

@bot.message_handler(commands=['start'])
def send_welcome(message):
    markup = types.ReplyKeyboardMarkup()
    itembtn1 = types.KeyboardButton('اختر اللون الأحمر🔴')
    itembtn2 = types.KeyboardButton('اختر اللون الأخضر🟢')
    itembtn3 = types.KeyboardButton('اختر اللون الأزرق 🔵')
    markup.row(itembtn1, itembtn2, itembtn3)
    bot.send_message(message.chat.id, "مرحبًا ، يرجى اختيار لون:", reply_markup=markup)

@bot.message_handler(func=lambda message: True)
def echo_all(message):
    bot.reply_to(message, message.text)

bot.polling()
