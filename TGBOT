import nest_asyncio nest_asyncio.apply()

from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup from telegram.ext import ApplicationBuilder, CommandHandler, CallbackQueryHandler, ContextTypes import random import json import os

Загрузка слов

words = { "apple": "яблоко", "cat": "кот", "dog": "собака", "sun": "солнце", "water": "вода", "pen": "ручка", "book": "книга", "table": "стол", "chair": "стул", "window": "окно", "door": "дверь", "school": "школа", "student": "ученик", "teacher": "учитель", "car": "машина", "bus": "автобус", "train": "поезд", "plane": "самолет", "food": "еда", "bread": "хлеб", "milk": "молоко", "cheese": "сыр", "butter": "масло", "egg": "яйцо", "sugar": "сахар", "salt": "соль", "pepper": "перец", "meat": "мясо", "fish": "рыба", "chicken": "курица", "coffee": "кофе", "tea": "чай", "juice": "сок", "banana": "банан", "orange": "апельсин", "grape": "виноград", "lemon": "лимон", "peach": "персик", "pear": "груша", "plum": "слива", "computer": "компьютер", "keyboard": "клавиатура", "mouse": "мышь", "screen": "экран", "phone": "телефон", "camera": "камера", "clock": "часы", "watch": "наручные часы", "bag": "сумка", "box": "коробка", "tree": "дерево", "flower": "цветок", "grass": "трава", "sky": "небо", "star": "звезда", "moon": "луна", "earth": "земля", "fire": "огонь", "air": "воздух", "wind": "ветер", "rain": "дождь", "snow": "снег", "ice": "лед", "cold": "холодно", "hot": "жарко", "warm": "тепло", "day": "день", "night": "ночь", "morning": "утро", "evening": "вечер", "boy": "мальчик", "girl": "девочка", "man": "мужчина", "woman": "женщина", "child": "ребенок", "friend": "друг", "family": "семья", "mother": "мать", "father": "отец", "brother": "брат", "sister": "сестра", "uncle": "дядя", "aunt": "тётя", "cousin": "двоюродный брат/сестра", "grandmother": "бабушка", "grandfather": "дедушка", "baby": "малыш", "person": "человек", "people": "люди", "name": "имя", "city": "город", "village": "деревня", "country": "страна", "street": "улица", "house": "дом", "room": "комната", "wall": "стена", "floor": "пол", "ceiling": "потолок", "roof": "крыша", "complicated": "сложный",
"consequence": "последствие",
"environment": "окружающая среда",
"responsibility": "ответственность",
"opportunity": "возможность",
"conversation": "разговор",
"immediately": "немедленно",
"experience": "опыт",
"unfortunately": "к сожалению",
"successful": "успешный",
"improvement": "улучшение",
"disappointment": "разочарование",
"relationship": "отношение",
"achievement": "достижение",
"communication": "коммуникация",
"recommendation": "рекомендация",
"knowledge": "знание",
"temperature": "температура",
"government": "правительство",
"information": "информация",
"development": "развитие",
"independent": "независимый",
"understanding": "понимание",
"international": "международный",
"organization": "организация",
"investment": "инвестиция",
"opinion": "мнение",
"education": "образование",
"technology": "технология",
"definition": "определение",
"opposition": "противостояние",
"circumstance": "обстоятельство",
"motivation": "мотивация",
"contribution": "вклад",
"announcement": "объявление",
"recommend": "рекомендовать",
"participation": "участие",
"accommodation": "жильё",
"competition": "соревнование",
"possibility": "возможность",
"confusion": "путаница",
"transportation": "транспорт",
"preparation": "подготовка",
"celebration": "празднование",
"compromise": "компромисс",
"negotiation": "переговоры",
"explanation": "объяснение",
"advertisement": "реклама",
"exaggeration": "преувеличение",
"determination": "решимость",
"reliability": "надёжность",
"permission": "разрешение",
"prevention": "предотвращение",
"requirement": "требование",
"announcement": "объявление",
"arrangement": "договоренность",
"cancellation": "отмена",
"collaboration": "сотрудничество",
"complication": "осложнение",
"consideration": "рассмотрение",
"continuation": "продолжение",
"cooperation": "сотрудничество",
"criticism": "критика",
"demonstration": "демонстрация",
"destination": "пункт назначения",
"discovery": "открытие",
"discussion": "обсуждение",
"distribution": "распределение",
"emergency": "чрезвычайная ситуация",
"entertainment": "развлечение",
"equipment": "оборудование",
"evaluation": "оценка",
"exception": "исключение",
"existence": "существование",
"explanation": "объяснение",
"fascination": "увлечение",
"flexibility": "гибкость",
"foundation": "основание",
"generation": "поколение",
"hospitality": "гостеприимство",
"imagination": "воображение",
"implementation": "реализация",
"inconvenience": "неудобство",
"influence": "влияние",
"ingredient": "ингредиент",
"injury": "травма",
"intelligence": "интеллект",
"interpretation": "толкование",
"interruption": "перебой",
"introduction": "введение",
"investigation": "расследование",
"invitation": "приглашение",
"leadership": "лидерство",
"maintenance": "техническое обслуживание",
"management": "управление",
"measurement": "измерение",
"movement": "движение",
"observation": "наблюдение",
"occupation": "занятие",
"organization": "организация",
"participation": "участие",
"partnership": "партнёрство",
"performance": "исполнение",
"permission": "разрешение",
"personality": "личность",
"preference": "предпочтение",
"preparation": "подготовка",
"presentation": "презентация",
"priority": "приоритет",
"production": "производство",
"profession": "профессия",
"protection": "защита",
"qualification": "квалификация",
"recognition": "признание",
"reduction": "сокращение",
"relationship": "отношение",
"replacement": "замена",
"requirement": "требование",
"research": "исследование",
"resistance": "сопротивление",
"resolution": "решение",
"responsibility": "ответственность",
"satisfaction": "удовлетворение",
"selection": "выбор",
"significance": "значение",
"suggestion": "предложение",
"surprise": "сюрприз",
"suspicion": "подозрение",
"temperature": "температура",
"tradition": "традиция",
"transportation": "транспортировка",
"understanding": "понимание",
"variety": "разнообразие",
"achievement": "достижение",
"adjustment": "регулировка",
"advantage": "преимущество",
"alternative": "альтернатива",
"atmosphere": "атмосфера",
"awareness": "осведомлённость",
"background": "предпосылка",
"boredom": "скука",
"capacity": "вместимость",
"challenge": "вызов",
"characteristic": "характеристика",
"circumstance": "обстоятельство",
"commitment": "обязательство",
"community": "сообщество",
"comparison": "сравнение",
"composition": "состав",
"conclusion": "вывод",
"condition": "условие",
"connection": "связь",
"construction": "строительство",
"contribution": "вклад",
"creativity": "креативность",
"curiosity": "любознательность",
"declaration": "заявление",
"departure": "отъезд",
"destruction": "разрушение",
"difference": "разница",
"distraction": "отвлечение",
"efficiency": "эффективность",
"election": "выборы",
"emphasis": "акцент",
"encouragement": "поощрение",
"enthusiasm": "энтузиазм",
"evidence": "доказательство",
"excitement": "волнение",
"expansion": "расширение",
"expectation": "ожидание",
"expenditure": "расход",
"failure": "неудача",
"familiarity": "знакомство",
"foundation": "фундамент",
"friendship": "дружба",
"guidance": "руководство",
"hesitation": "колебание",
"hostility": "враждебность",
"identification": "идентификация",
"ignorance": "невежество",
"impression": "впечатление",
"indication": "указание",
"instruction": "инструкция",
"intention": "намерение",
"interference": "вмешательство",
"knowledge": "знание",
"leadership": "лидерство",
"limitation": "ограничение",
"location": "местоположение",
"maintenance": "обслуживание",
"misunderstanding": "недоразумение",
"necessity": "необходимость",
"neglect": "пренебрежение",
"obligation": "обязательство",
"observation": "наблюдение",
"opinion": "мнение",
"patience": "терпение",
"perception": "восприятие",
"permission": "разрешение",
"possibility": "возможность",
"preparation": "подготовка",
"presentation": "представление",
"prevention": "предотвращение",
"principle": "принцип",
"probability": "вероятность",
"proposal": "предложение",
"recognition": "узнавание",
"reliability": "надёжность",
"replacement": "замена",
"requirement": "требование",
"responsibility": "ответственность",
"restriction": "ограничение",
"selection": "отбор",
"significance": "важность",
"statement": "заявление",
"structure": "структура",
"survival": "выживание",
"tendency": "склонность",
"transition": "переход",
"variation": "изменение",
"willingness": "готовность"}

Команда /start

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE): await update.message.reply_text("Привет! Нажми /quiz чтобы начать викторину с вариантами.")

Команда /quiz

async def quiz(update: Update, context: ContextTypes.DEFAULT_TYPE): word, correct_answer = random.choice(list(words.items())) context.user_data["correct_answer"] = correct_answer context.user_data["current_word"] = word

options = list(set(words.values()) - {correct_answer})
random.shuffle(options)
options = options[:3] + [correct_answer]
random.shuffle(options)

keyboard = [[InlineKeyboardButton(text=opt, callback_data=opt)] for opt in options]
reply_markup = InlineKeyboardMarkup(keyboard)
await update.message.reply_text(f"Что значит слово: {word}?", reply_markup=reply_markup)

Обработка кнопки

async def button(update: Update, context: ContextTypes.DEFAULT_TYPE): query = update.callback_query await query.answer()

selected = query.data
correct = context.user_data.get("correct_answer")
if selected == correct:
await query.edit_message_text(f"✅Правильно! Так держать👍 Это: {correct}")
else:
await query.edit_message_text(f"❌Неправильно. Попытайся ещё 😢 Правильный ответ: {correct}")

Запуск

async def main(): app = ApplicationBuilder().token("7864251012:AAFTWFdQlq4Kfy1_yue-QVco7En3oNBirVs").build()

app.add_handler(CommandHandler("start", start))
app.add_handler(CommandHandler("quiz", quiz))
app.add_handler(CallbackQueryHandler(button))
print("Бот запущен")
await app.run_polling()

import asyncio asyncio.run(main())

...твой существующий код выше
Кнопка для доната
donate_keyboard = InlineKeyboardMarkup(
inline_keyboard=[
[InlineKeyboardButton(text="Поддержать бота", url="https://www.donationalerts.com/r/https://www.donationalerts.com/widget/goal/8710269?token=QYnsajj5tZgqi8AKPnxm")]
]
)

Команда /donate
@dp.message_handler(commands=['donate'])
async def donate(message: types.Message):
await message.answer("Если хочешь поддержать проект — нажми кнопку ниже, брат🤝:", reply_markup=donate_keyboard)

У тебя уже должен быть executor.start_polling(dp) в конце — оставь как есть

