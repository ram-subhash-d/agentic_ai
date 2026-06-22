There are 2 kinds of prompts
* System prompt : This prompt is given by the developer to the LLM. Setting up the context, role and limits of the LLM for that agent.
* User prompt : This is the prompt given by the end user of the agent, passed to the LLM. These can be any questions being asked while the agent is being used.  

Both the prompts contain components which are discussed below.

# Prompt components
We can break the prompt into 3 components to make it structured and get the expected answers.
* Instruction : Tell the model how to answer the questions.
* Context : External information or additional context that can steer the model to better responses. Context can come from vector databases.
* Input data : The input or question that we are insterested to find a response for.  

**Example:**  
Answer the question on the context below. Keep the answer short and concise. Respond "Unsure about answer" if not sure about the answer.

Teplizumab traces its roots to a New jersey drug company called Ortho Pharmaceutical. There ...

What was OKT3 originally sourced from?

There is another well known structure, that breaks the prompt into 5 components, known as the CRAFT structure.
* Context : Background information and what is the situation.
* Role : Person or expertise, who is the LLM, what assitant.
* Action : Specific task to be performed, what to do.
* Format : Output structure, what should it look like.
* Target audience : Who comsume the output, tone and vacabulary.

# Zero shot, one shot and few shot
Shot here is like a example.
* Zero shot : In the above example, we have given the plain instructions, along with the context and question, this is know as zero shot.
* One shot : Sometime times the tasks are complex enough, that it is not able to follow the plain instructions, we have to supply it a example, this is called one shot.
* Few shot : Here we suppy more than one example, a few of them, for more complex tasks, to get better responses.

**Example:**  
Classify the test into neutral, negative or positive  

This is awesome! // Positive  
This is bad! //Negtive  
Wow that movie was rad! //Positive  

I think the food was ok

# Chain-of-thought(CoT) prompting
This is where you will be listing the steps to the LLM to solve the problem, for concepts like math where it is weak at or for very complex tasks. Example below.

**Standard prompting**  
**Model input**  
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?  

A: The answer is 11.

Q: The cafeteria had 23 apples. If they used 20 to make lunch and bought 6 more, how many apples do they have?

**Model output**  
A: The answer is 27 (which is wrong)

**Chain-of-thought prompting**  
**Model input**  
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 tennis balls. How many tennis balls does he have now?  

A: Roger started with 5 balls. 2 cans of 3 tennis balls each is 6 tennis balls. 5 + 6 = 11. The answer is 11.

Q: The cafeteria had 23 apples. If they used 20 to make lunch and bought 6 more, how many apples do they have?

**Model output**  
A: The cafetaria had 23 apples originally. They used 20 to make lunch. So they had 23 - 20 = 3. They bought 6 maore apples, so they have 3 + 6 = 9. The answer is 9.

# ReAct: Reason + Act
The examples we discussed so far are single iteration, one LLM call and it answers. It does not have the option to interact with the user. Like model saying that it does not have enough information and needs you to supply more information or ask you more questions.  
In react prompting, it mixes acting with reasoning and interaction with external environment.

**Example:**  
Aside from the Apple Remote, what other devices can control the program Apple Remote was originally designed to interact with?

**ReAct - Multiple LLM call's**  
Thought 1: I need to search Apple Remote and find the program it was originally designed to interact with.
Act 1: Search[Apple Remote]
Obs 1: The Apple Remote is a remote control introduced in October 2005 by Apple...originally designed to control the Front Row media center program...

Thought 2: Apple Remote was originally designed to control the Front Row media center program. I need to search Front Row next and find what other devices can control it.
Act 2: Search[Front Row]
Obs 2: Could not find [Front Row]. Similar: [Front Row Seat to Earth, Front Row Motorsports, Front Row (software), ...]

Thought 3: Front Row is not found. I need to search Front Row (software).
Act 3: Search[Front Row (software)]
Obs 3: Front Row is a discontinued media center software...

Thought 4: Front Row (software) is controlled by an Apple Remote or the keyboard function keys. So the answer is keyboard function keys.
Act 4: Finish[keyboard function keys]

These iterations are planned and execute by the LLM behind the scenes.