# PromptBrake AI assistant skill

`promptbrake-free-tools/` is a portable instruction package for all four hosted
PromptBrake MCP tools: injection payloads, OWASP risk mapping, ADLC release planning,
and custom response test packs. It contains no PromptBrake server implementation.

## Use

With Node.js installed, run this in the project where you want the skill:

```sh
npx skills add AJ888/promptbrake-skills --skill promptbrake-free-tools
```

Choose your supported assistant in the installer. This installs the instructions
and examples; connect the MCP server separately as described below. Alternatively,
install the complete folder manually.

1. Connect your assistant's remote MCP client to `https://promptbrake.com/free-tools/mcp`
   with authentication set to none. See https://promptbrake.com/free-tools for setup.
2. Install the complete `promptbrake-free-tools` folder in your client's supported
   skills directory. Keep `references/` beside `SKILL.md`. For Codex, the personal
   skills directory is `~/.codex/skills/` (or `$CODEX_HOME/skills`). Other clients must
   support both skills and remote MCP; MCP support alone does not install a skill.
3. Invoke `promptbrake-free-tools` using your client's skill mechanism, or ask for
   a relevant task. In Codex, use `$promptbrake-free-tools`.

Examples:

- “Get retrieval-based prompt-injection inputs for my support RAG system.”
- “Map prompt-injection risk to test ideas and review responsibilities.”
- “Help me plan the release of my tool-calling agent; keep unknown decisions explicit.”
- “Build a test pack from my chatbot's expected and forbidden response text.”

The free tools prepare inputs and artifacts. Running tests requires a configured
PromptBrake runner and CI access. Text comparisons cannot verify backend actions;
release plans are not security certification.

## Public package

Public repository: https://github.com/AJ888/promptbrake-skills

The `promptbrake-free-tools/` directory is the installable skill. Only these skill
instructions, examples, and this setup guide belong in the public package.
