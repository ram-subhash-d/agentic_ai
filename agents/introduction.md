AI agent is a system that can perceive its environment, make decisions and take actions to acheive a goal, often autonomously.
* Perceive environment : Understand instructions.
* Make decision : Run a search, use a tool etc.
* Take action : Tools, API's, databases, function call etc.
* Adopts behaviour based on results or feadback : Like the agent may use the worng tool, it will retry using another tool.

Traditional software has intellicense in the form of if-else and logic, agent uses LLM for intellicense.  
It does all of these autonomously, without us telling it to follow a predefined path.

Agents plan, decide, act, observe outcomes and iterate.

# The core concept
* You provide the tools: You tell the model, "I have a function called get_weather(city) that takes a city name as an argument."
* The model "thinks": If a user asks, "What's the weather in Tokyo?", the model recognizes that your tool can solve this.
* The model outputs JSON (not text): Instead of replying to the user, the model pauses and gives you a structured request: {"function": "get_weather", "arguments": {"city": "Tokyo"}}.
* You execute: Your code sees this request, runs the actual Python function, and gets the result (e.g., "Sunny, 25°C").
* The model finishes: You feed that result back to the model, and it writes the final natural language answer: "It is currently sunny and 25 degrees in Tokyo."

# Machine learning vs Generative AI
Machine learning learns patterns from data and then does classification, prediction etc. Its powerful but a narrow one model per one specific task approach.  
Generative AI is about generating text, code and images using LLM's. It is general purpose, the same LLM's will be used by various agents for different applications.  
Modern LLM's are trained on massive data sets to gain general knowledge and built on transformer architectures. LLM's can be called using client libs or through REST API.

# LLM's use text completion scheme
The LLM will try to expect the next few characters and try to complete the sentance. For example we can tell the model in the user prompt, what you are expecting from it, then give the text, the model will complete it with a answer. We can specify the desired format in instructions, then tell it what we are expecting form it. It is good to start a conversation with instructions, as these model are trained to follow instructions, it is called instruction tuning.