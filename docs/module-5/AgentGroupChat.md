What is AgentGroupChat?
Think of it like a group WhatsApp chat — but instead of people, you have smart AI agents talking to each other to solve a problem or complete a task.

🛠️ How to Create a Group Chat for Agents
You can make a chat in two ways:

✅ Option 1: Create chat with agents already added
python
Copy
Edit
agent_writer = AzureAIAgent(...)
agent_reviewer = AzureAIAgent(...)

chat = AgentGroupChat(agents=[agent_writer, agent_reviewer])
✅ Option 2: Start empty and add agents later
python
Copy
Edit
chat = AgentGroupChat()

chat.add_agent(agent=agent_writer)
chat.add_agent(agent=agent_reviewer)
💬 Add a Message to the Chat
Now you (the user) send a message to the agent group like this:

python
Copy
Edit
chat_message = ChatMessageContent(role=AuthorRole.USER, content="Please write and review a paragraph.")
await chat.add_chat_message(message=chat_message)
🧠 Chat Modes: Single-Turn vs Multi-Turn
🔹 Single-Turn Chat
Only one agent responds to the user’s message.

python
Copy
Edit
async for message in chat.invoke(agent_writer):
    # process agent_writer's reply
🔹 Multi-Turn Chat
Agents take turns responding. One might write something, another might review it, and they keep chatting until they’re done.

python
Copy
Edit
async for message in chat.invoke():
    # process multiple agents’ responses as they happen
🤝 Why is this Useful?
Agents can collaborate like a team.

They build on each other’s responses.

You get smarter, more complete answers without doing the work yourself.

🧠 Real-Life Example
Suppose you ask:

"Write a blog post and review it."

📝 Writer Agent writes the blog.

✅ Reviewer Agent checks for grammar and quality.

🧠 They talk in the group chat, improving the content together.

