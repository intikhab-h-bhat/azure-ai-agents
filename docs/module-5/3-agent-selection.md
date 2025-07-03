# What is Agent Selection?
In a multi-agent chat, you need to decide which agent should respond next.

## Example:
👨‍💻 CopywriterAgent – Good at writing content.
🎨 ReviewingDirectorAgent – Good at reviewing content.
If the user says, “Write a slogan for a scrubbing brush”, the system should pick the Copywriter, not the reviewer.

# ✅ Why is Agent Selection Important?
- Accuracy – Right agent gives the best answer.
- Efficiency – No need to involve all agents unnecessarily.
- Scalability – Helps manage many agents smoothly.

# 🧠 How Does the Framework Pick the Right Agent?
- 🔹 Single-Turn (One message and response)
Uses intent recognition (figures out what the user wants).
Follows rules you define (e.g., “slogan → Copywriter”).

- 🔹 Multi-Turn (Back-and-forth conversation)
Keeps track of chat history.
Can switch agents when the topic changes.

# 🎯 How to Design Agent Selection?
You use a strategy to control how agents take turns in a group chat.
There are three main strategies:
## 1. SequentialSelectionStrategy
Agents take turns in the order you added them.

### Example:
User talks → Copywriter replies
Then → Reviewer replies
Then → Copywriter again
(Repeats)

## 2. KernelFunctionSelectionStrategy
This lets you write a custom prompt to decide who talks next, based on chat history.
### Example prompt:

```python
After user input → CopywriterAgent replies  
After CopywriterAgent → ReviewingDirectorAgent replies  
After ReviewingDirectorAgent → CopywriterAgent replies again
```
You can also shorten the chat history used (called chat history truncation) to make it faster and save resources.

## 3. Custom Strategy (SelectionStrategy Class)
You can create your own custom logic by writing a select_agent() function.
Example:
```python
If the last message was a question → Let Copywriter answer  
If it's feedback → Let Reviewer answer
```
Then assign this strategy when setting up the chat:

```python
chat = AgentGroupChat(selection_strategy=my_strategy)```
```

# 📉 Truncating Chat History (Optional)
To save memory or cost:
- Only use the last 1 or 2 messages to choose the next agent.
- You can set this using ChatHistoryTruncationReducer(target_count=1)

✅ Summary
|Feature	|What it Does|
|-----|-----|
|Agent Selection	|Chooses the best agent to respond|
|Sequential Strategy	| Agents take turns in order|
|Kernel Function Strategy	|You write a smart rule (prompt) to choose|
|Custom Strategy	|You write full code to decide|
|Truncating History	|Keeps only a few messages to improve performance|

