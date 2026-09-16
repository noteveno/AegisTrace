# Install AegisTrace with an AI coding agent

Copy the prompt below into Codex, Claude Code, OpenCode, or another coding agent that can access your terminal. The agent will identify its own environment where possible and install the skill locally. It should never need administrator privileges.

```text
Install the AegisTrace skill from https://github.com/noteveno/AegisTrace on this computer.

First, determine which coding-agent environment you are operating in. Install the repository's `skills/aegistrace` directory into the most appropriate personal skill location:

- Codex: ~/.codex/skills/aegistrace
- Claude Code: ~/.claude/skills/aegistrace
- OpenCode: ~/.config/opencode/skills/aegistrace
- Another Agent Skills-compatible tool: use its documented personal skill directory; if unknown, explain the available options instead of guessing.

Rules:
- Do not use sudo or modify any project files.
- Check whether the destination already exists. If it does, show its current state and ask me before replacing it.
- Clone or download the repository into a safe temporary directory, copy only `skills/aegistrace` into the chosen destination, and remove the temporary copy afterward.
- Verify that the installed file is `<destination>/SKILL.md` and that it has valid YAML frontmatter.
- Tell me the final installation path and exactly how to invoke the skill in this agent.
```

## If your agent cannot use the terminal

Clone or download the repository, then copy its `skills/aegistrace` folder to the matching location in the prompt above. Restart the coding agent if it does not detect newly added personal skills automatically.
