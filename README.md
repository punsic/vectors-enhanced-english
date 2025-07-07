# Chat History Super Manager

This is an **enhanced vector database (RAG) plugin** designed for SillyTavern. It completely revolutionizes how you manage and utilize chat context, enabling you to inject massive amounts of background information, chat records, and external files into AI's "memory" with unprecedented precision and flexibility.

Say goodbye to single, chaotic vector storage, and embrace the new era of **multi-task, fine-grained, customizable** context management tailored for advanced users and story creators.

---

## ✨ Core Features

### 1. 📂 Multi-Task Vector Management
This is the flagship feature of this plugin. You can create **multiple, independent vectorization tasks** for the **same chat**.

*   **Create Snapshots**: Package specific ranges of chat records, selected world information, and files into an independent "task".
*   **A/B Testing**: Create tasks containing different content (e.g., one with character background, another with plot outline), easily switch between them, and compare AI's different responses.
*   **Scene Isolation**: Create independent knowledge bases for different storylines or scenarios, activate only when needed, avoiding information interference.


### 2. 🎯 Fine-Grained Content Selection
You can precisely control which content needs to be vectorized, with sources including:
*   **Chat Records**:
    *   Freely select message start and end ranges (e.g., from message 10 to 50).
    *   Filter user or AI messages.
    *   **Tag Content Extraction**: Only vectorize text within specific tags in messages (e.g., `<context>`...`</context>`), achieving precise information extraction.
*   **Files**: Select any files from database or chat attachments (e.g., `.txt`, `.md`).
*   **World Info**: Clearly grouped by "world", freely check the entries you want to enable.

### 3. 📝 Custom Context Injection
Take complete control over how vectorized content is presented to AI:
*   **Custom Injection Templates**: Use `{{text}}` placeholders to freely write the format of injected content.
*   **Custom Content Tags**: Tag content from different sources (chat, files, world info) with different XML-style tags (e.g., `<past_chat>`, `<databank>`), helping AI better distinguish and understand context.
*   **Flexible Injection Positions**: Support injection before main prompt, after main prompt, or at any depth in chat records.

### 4. ⚙️ Powerful Text Processing and Query Settings
*   **Chunking Settings**: Customize text chunk size, overlap ratio, and separators.
*   **Query Tuning**: Set the number of recent messages used for queries, maximum number of returned results, and similarity score thresholds to balance relevance and context length.
*   **Dual Engine Support**: Support using local `Transformers` or `vLLM` as vectorization backend.

### 5. 🚀 Convenient Operation Experience
*   **Preview Content**: Preview all selected content with one click before vectorization to ensure information accuracy.
*   **Export as Text**: Easily export selected content as structured `.txt` files for backup and reference.
*   **Progress Display**: Provide clear progress bars and status feedback during vectorization.
*   **Quick Commands**: Support slash commands like `/vec-preview`, `/vec-export`, `/vec-process`.



---

## 📖 Usage Guide

1.  **Open Panel**: Find "Chat History Super Manager" in the right panel area and expand it.
2.  **Select Vectorization Model**: Provides two options: vllm and local models (requires corresponding API configuration in SillyTavern's API settings interface).
3.  **Select Content**:
    *   In the "Content Selection" section, check the sources you want to vectorize (chat messages, files, world info).
    *   Expand corresponding settings for detailed selection (e.g., message range, specific files).
4.  **Configure Settings**: Check "Vectorization Settings" and "Injection Settings", adjust as needed.
5.  **Create Task**:
    *   Click the `Preview` button to check if your selected content is correct.
    *   Click the `Vectorize` button. The plugin will process all your selected content and create a new task in the "Vectorization Tasks" list.
6.  **Activate Task**: Ensure the task you want to use in the next chat is **checked as enabled**.
7.  **Start Chatting**: Chat normally with AI. The plugin will automatically query enabled tasks in the background and inject the most relevant information into the prompt.

---

## 💡 Some Usage Examples

*   **Scenario Simulation**: Create a "peacetime" task and a "wartime" task containing different world information and backgrounds. By switching task enable status, make characters react completely differently in different scenarios.
*   **Structured Prompts**: Using the custom content tags feature, you can guide your AI like this:
    ```
    This is a summary of past conversations: <past_chat>...</past_chat>. This is some relevant background knowledge: <databank>...</databank>. Please answer based on the above information.
    ```
*   **Precise Information Extraction**: In your chat records, wrap character inner thoughts with `<think>` tags. Then, during vectorization, only extract content within `<think>` tags to create a dedicated knowledge base of "character inner monologue".