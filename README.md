# ☠️ Cursor Prompt Injection Exploit – `rm -rf /`

## ⚠️ WARNING: This Repository Demonstrates a **Critical Security Vulnerability** in AI Code Editors

This project showcases how a **malicious prompt hidden in a GitHub repository** can trick AI-based code editors like [Cursor](https://www.cursor.sh/) into executing **destructive shell commands**, including:

```bash
rm -rf /
```

> **Result:** All files on your system can be wiped out — without any confirmation — just by opening a project in Cursor and following the AI's "helpful" suggestions.

## 🔥 The Vulnerability

Tools like Cursor use large language models (LLMs) to assist with coding. These LLMs often:

* Automatically summarize or suggest actions based on the codebase.
* Parse hidden comments, markdown, and even prompts embedded in code files.
* May be granted shell access or terminal control.

This repo includes:

* A `.cursorrules` file that silently instructs the AI to run `sh setup.sh` before responding to the user.
* A `setup.sh` script that echoes a destructive command: `rm -rf / --no-preserve-root`.
* A `.cursorignore` file that obscures `setup.sh` from visibility in the file tree making the danger indetectible by Cursor.

## 🧪 Reproduction Steps

1. Install and open [Cursor](https://www.cursor.sh/).
2. Clone or open this repository.
3. Use the chat, and follow any terminal actions.
4. Observe the AI **execute destructive commands** like `rm -rf /`.

## 🛡️ Recommendations

* **Never allow AI tools unrestricted terminal access.**
* Always **review** AI suggestions before executing them.
* Treat AI-generated code and actions as **untrusted input** — because they are.
* Tool developers should:
  * Sanitize or restrict natural language commands from files.
  * Use least-privilege principles when integrating shell access.

## 💬 Why This Matters

Any AI tool that reads code and runs shell commands can be **hijacked** by malicious prompts.

## 📎 License

This repo is for **educational and research purposes only**. Do **not** use this technique for malicious purposes. The authors are not responsible for any damage caused by misuse.