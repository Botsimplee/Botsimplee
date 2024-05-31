import telebot
bot = telebot.TeleBot(7214165932:AAGWp5gHfKjj8lUOYeX8qh4DzHw0zqXTKSQ)


- 👋 Hi, I’m @predictionDadBot
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Botsimplee/Botsimplee is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import requests

def get_wikipedia_summary(query: str) -> str:
    url = f"https://en.wikipedia.org/api/rest_v1/page/summary/{query.replace(' ', '_')}"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        return data.get("extract", "I couldn't find any information on that topic.")
    else:
        return "There was an error fetching data from Wikipedia."

def get_response(message: str) -> str:
    if "math" in message.lower():
        return get_wikipedia_summary("Mathematics")
    elif "science" in message.lower():
        return get_wikipedia_summary("Science")
    else:
        return "I'm here to help with knowledge and education. Ask me anything!"
