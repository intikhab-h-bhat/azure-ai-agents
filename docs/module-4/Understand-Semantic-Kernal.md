## AI Service Connectors:
- These are like adapters that let your code talk to different AI services (like ChatGPT, Azure OpenAI, etc.) using a single, unified way. This means you can easily switch between different AI providers for things like chat, text generation, or image generation without changing your main code.

## Memory Connectors (Vector Store Connectors):
- These let your application connect to different kinds of memory storage systems (like databases that store information as vectors, such as Qdrant or Chroma). This is useful for remembering things, searching past conversations, or storing knowledge that the AI can use later.

## Functions and Plugins:
- Plugins are containers that hold one or more functions. These functions can do specific tasks or calculations. Once you register a plugin with the kernel, the AI can use these functions when needed, either by calling them directly or by including them in a prompt.

## Prompt Templates:
- Think of these as reusable forms or blueprints for how you want to ask the AI something. A prompt template can combine instructions, user input, and the results from functions to create a dynamic, flexible prompt for the AI to respond to.

## Filters:
- Filters are like checkpoints that let you run custom code before or after a function or prompt is used. For example, you could use a filter to log information, check for errors, or modify the input/output. Function filters wrap around functions, and prompt filters wrap around prompts.

### In summary:
Semantic Kernel is built from building blocks that help you connect to AI services, store and retrieve information, organize reusable functions, create flexible prompts, and customize how everything runs—making it easier to build smart, adaptable AI applications
