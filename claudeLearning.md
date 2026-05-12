Your markdown notes on the technical information and commands for using **Claude Code** (the agentic terminal tool from Anthropic), as presented in the video by Mosh Hamadani, are ready below.

### Claude Code: Technical Reference Guide

Claude Code is an **agentic coding tool** that lives in your terminal. Unlike a standard chat interface, it has permission to read/write files, execute bash commands, run tests, and manage git workflows autonomously.

---

#### 1. Installation & Setup

To install Claude Code on your system, use the following commands based on your OS:

- **Mac / Linux / WSL:**

```bash
curl -fsSL https://code.anthropic.com/install.sh | sh

```

- **Windows (PowerShell):**

```powershell
irm https://code.anthropic.com/install.ps1 | iex

```

- **Adding to Path:** After installation, if you see a warning, follow the terminal instructions to add `claude` to your system's PATH environment variable.

---

#### 2. Project Initialization

- **`/init`**: This is the most critical command for a new project. It creates a `claude.md` file.
- **`claude.md`**: Acts as the project's **Long-Term Memory**. It contains architectural decisions, tech stacks, and project-specific instructions that are sent with every prompt to keep Claude "in context."

---

#### 3. Core Slash Commands

These commands are built-in functions to manage the Claude session:

- **`/model`**: View or change the active LLM (e.g., Claude 3.5 Sonnet, Claude 3 Opus).
- **`/terminal-setup`**: (or `/ter`) Installs the **Shift + Enter** keybinding, allowing you to write multi-line prompts without accidentally sending the message.
- **`/tasks`**: Displays current background tasks (like a running dev server). You can kill tasks from this view.
- **`/context`**: Visualizes the current context window usage (tokens used vs. total capacity).
- **`/compact`**: Clears the conversation history but keeps a high-level summary to free up token space without losing project progress.
- **`/clear`**: Wipes the current short-term memory (conversation history). Recommended when switching to a completely unrelated task.
- **`/usage`**: (For subscribers) Shows your remaining quota for the week/session.
- **`/cost`**: (For API users) Displays the monetary cost incurred during the current session.

---

#### 4. Inline Symbols & Shortcuts

- **`!` (Exclamation Mark)**: Prefix for running **Bash/Shell commands** directly inside the Claude terminal (e.g., `!npm install`).
- **`@` (At Sign)**: Used to reference specific **files or folders** to give Claude explicit context (e.g., `@app.jsx fix the bug`).
- **`&` (Ampersand)**: Used to run a command as a **background job**.
- **`?` (Question Mark)**: Displays a quick help menu with all available shortcuts.
- **`Ctrl + L`**: Clears the terminal screen.
- **`Shift + Tab`**: Cycles through **Modes**:

1. **Normal Mode**: Claude asks for permission before every file edit.
2. **Accept Edits On**: Claude edits files automatically (best for multi-file refactoring).
3. **Plan Mode**: Claude drafts an implementation plan for approval before touching any code.

---

#### 5. Operating Modes

- **Plan Mode**: Used for complex features. Claude analyzes the codebase and provides a step-by-step checklist of changes. You can refine the plan before execution.
- **Execution Mode**: Once a plan is approved (or in Normal mode), Claude uses the **Write Tool** to modify code and the **Bash Tool** to run tests or install dependencies.

---

#### 6. Key Technical Workflow Concepts

- **Agentic Tools**: Claude uses specific "tools" to interact with your OS:
- `ls`: List files.
- `read`: View file content.
- `write`: Edit or create files.
- `bash`: Execute terminal commands.

- **MCP (Model Context Protocol)**: A standard that allows you to extend Claude with external integrations like GitHub (to manage issues), Google Drive, or Slack.
- **Checkpoints**: Claude creates internal checkpoints, allowing you to undo large-scale automated changes if the generated code is incorrect.
- **Context Management**: It is vital to `clear` or `compact` regularly. If the context window (200k tokens) fills up, Claude may begin to "hallucinate" or forget earlier architectural constraints.


In Claude Code, skills.md is a configuration file used to store custom reusable instructions or "tools" that you want Claude to remember across different sessions.

Key Uses:
Persistent Custom Tools: You can define specific workflows (like "how to run my custom test suite") that Claude will treat as a built-in capability.

Task Automation: It allows you to create "shorthand" commands for complex, repetitive terminal sequences.

Behavioral Guidance: While claude.md is for project-specific facts, skills.md is for how you want Claude to perform technical actions (e.g., "Always use pnpm instead of npm" or "Format my code using this specific linter command").

In short: If claude.md is the project’s memory, skills.md is the agent’s technical training manual.

[file-tag: youtube-IuyVVtr1uhY]
