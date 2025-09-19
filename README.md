# Python-programming-2
Python programming about task . preparing a simple chatbot
import random
import datetime

# Define intents with possible keywords and responses
responses = {
    "greeting": {
        "keywords": ["hello", "hi", "hey", "good morning", "good evening"],
        "responses": ["Hi there!", "Hello!", "Hey!", "Greetings!"]
    },
    "farewell": {
        "keywords": ["bye", "goodbye", "see you", "exit"],
        "responses": ["Goodbye!", "See you soon!", "Take care!", "Chat later!"]
    },
    "how_are_you": {
        "keywords": ["how are you", "how's it going", "how do you do"],
        "responses": ["I'm just a bot, but I'm doing great!", "All systems go!", "Running smoothly!"]
    },
    "time": {
        "keywords": ["what time", "current time", "tell me the time"],
        "responses": []  # Will generate dynamically
    },
    "date": {
        "keywords": ["what date", "today's date", "current date"],
        "responses": []  # Will generate dynamically
    },
    "name": {
        "keywords": ["your name", "who are you"],
        "responses": ["I'm ChatBot 2.0!", "You can call me AssistantBot.", "I'm your virtual assistant."]
    },
    "joke": {
        "keywords": ["joke", "make me laugh", "funny"],
        "responses": [
            "Why don’t hospitals allow WiFi?Because they don’t want people pulling the plug just to get a stronger connection",
            "I told my computer I needed a break, and it said 'No problem – I’ll go to sleep.'",
            "What do you call 8 hobbits? A hob-byte!"
        ]
    },
    "default": {
        "responses": [
            "I'm not sure I understand.",
            "Can you rephrase that?",
            "I'm still learning, try asking something else."
        ]
    }
}

# Function to detect intent based on keywords
def get_intent(user_input):
    user_input = user_input.lower()
    for intent, data in responses.items():
        for keyword in data.get("keywords", []):
            if keyword in user_input:
                return intent
    return "default"

# Function to generate a response
def generate_response(intent):
    if intent == "time":
        return f"The current time is {datetime.datetime.now().strftime('%H:%M:%S')}."
    elif intent == "date":
        return f"Today's date is {datetime.datetime.now().strftime('%Y-%m-%d')}."
    else:
        return random.choice(responses[intent]["responses"])

# Chatbot main function
def chatbot():
    print("ChatBot 2.0: Hello! Ask me anything. Type 'bye' to exit.\n")

    while True:
        user_input = input("You: ").strip()

        if user_input.lower() in ["bye", "exit"]:
            print("ChatBot 2.0: Goodbye! Have a great day!")
            break

        intent = get_intent(user_input)
        response = generate_response(intent)
        print(f"ChatBot 2.0: {response}")

# Run the chatbot
chatbot()
