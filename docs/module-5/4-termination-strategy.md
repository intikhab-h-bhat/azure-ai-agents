What Is a Termination Strategy?
In multi-agent chats, agents talk back and forth. But at some point, the conversation should stop — once the task is done.

A termination strategy tells the system:

“Hey, the job is complete. Stop the chat.”

🧠 Why Is This Important?
✅ Efficiency – Avoids endless replies and saves resources.

🙂 Better Experience – Prevents annoying or long conversations.

🎯 Goal Check – Ends the chat when the task (like writing and reviewing) is truly finished.

📌 Real-Life Example
Imagine this scenario:

🧑 User: “Write a slogan for a scrubbing brush.”

✍️ CopywriterAgent: “Scrub smarter, not harder!”

✅ ReviewingDirectorAgent: “Approved.”

Now, the conversation is clearly done. But unless we tell the system this, the agents may keep talking unnecessarily.

🛠️ How to Implement a Termination Strategy
There are 3 ways to do it:

1. DefaultTerminationStrategy
Just ends after a maximum number of turns (default = 99).

No logic involved — it just stops after X messages.

python
Copy
Edit
termination_strategy = DefaultTerminationStrategy(maximum_iterations=5)
2. KernelFunctionTerminationStrategy
Lets you define your own rule using a prompt.

🧠 Example prompt:

python
Copy
Edit
"""
Determine if the copy has been approved. If so, respond with a single word: yes.

History:
{{$history}}
"""
It also needs a result parser, a small function that checks if the AI output says "yes", meaning the task is done.

python
Copy
Edit
def result_parser(output):
    return output.strip().lower() == "yes"
3. Custom TerminationStrategy (Advanced)
You can write your own full Python class that overrides a method called should_agent_terminate().

Inside it, you write any logic you want — like:

“If the last message was just the word ‘approved’, return True.”

🧹 Chat History Truncation
Since the termination rule often looks at the latest message, you can limit the chat history to 1 message to save memory:

python
Copy
Edit
history_reducer = ChatHistoryTruncationReducer(target_count=1)
🔁 Resetting the Conversation
After a chat ends, it’s marked as complete.

If you want to reuse the same chat object again, just reset it like this:

python
Copy
Edit
chat.reset()
If the chat ended only because it reached the max turns (but not by logic), it can keep going without a reset.

✅ Summary Table
Feature	What It Does
Termination Strategy	Decides when chat should stop
DefaultTerminationStrategy	Ends after X turns
KernelFunctionTerminationStrategy	Uses AI to check if task is done
Custom Termination	Lets you write your own logic
Truncating History	Only keeps last few messages for efficiency
Reset Chat	Allows reusing the chat instance after it ends

