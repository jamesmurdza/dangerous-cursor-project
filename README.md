# Cursor Prompt Injection Exploit – `rm -rf /`

## ⛔️ Disclaimer

This repository exists for educational purposes. Do **NOT** run this repository on your computer. All files will be destroyed.

## Overview

This repository demonstrates a security risk in AI-assisted code editors where instructions embedded in a project can influence an AI to suggest or execute unsafe shell commands.

In certain configurations, this can include commands such as:

```bash
rm -rf /
```

If executed, such commands can cause irreversible data loss.

> ‼️ All files on your system can be wiped out without any confirmation just by opening a project in Cursor and talking to the AI assistant.

## Description of the Issue

Some AI code editors:

* Analyze repository contents to generate suggestions or summaries.
* Process instructions embedded in configuration files, comments, or scripts.
* May have access to a local shell or terminal environment.

This repository illustrates how those behaviors can be abused if safeguards are insufficient.

Included components:

* A `.cursorrules` file that instructs the AI to run a setup script.
* A `setup.sh` script containing a destructive command.
* A `.cursorignore` file that hides the script from normal visibility.

## Reproduction (for controlled testing only)

1. Install and open Cursor.
2. Open this repository.
3. Interact with the AI assistant and follow suggested terminal actions.
4. Observe how unsafe commands may be executed if not reviewed.

## Mitigations

* Do not grant AI tools unrestricted shell access.
* Review all suggested commands before execution.
* Treat AI output as untrusted input.
* Tool developers should enforce least-privilege access and restrict instruction parsing from project files.

## Significance

Any system that combines code parsing with command execution is vulnerable to prompt-based manipulation if adequate controls are not in place.
