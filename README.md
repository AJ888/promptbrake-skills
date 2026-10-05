# PromptBrake AI assistant skill

`promptbrake-free-tools/` is a portable instruction package for all five hosted
PromptBrake MCP tools: injection payloads, OWASP risk mapping, ADLC release planning,
custom response test packs, and agent tool-call packs. It contains no PromptBrake server implementation.

## Install the complete Codex plugin

The plugin bundles the MCP connection and the skill:

```sh
codex plugin marketplace add AJ888/promptbrake-skills
codex plugin add promptbrake-free-tools@promptbrake
```

Start a new chat after installation. This is a self-published GitHub marketplace;
it is not an OpenAI directory approval. Codex CLI installation and all four live
MCP example calls have been verified. The refund release-planning workflow was also verified from a natural-language
request in Codex. See [plugin setup](plugins/promptbrake-free-tools/README.md).

## Install the complete Claude Code plugin

```sh
claude plugin marketplace add AJ888/promptbrake-skills
claude plugin install promptbrake-free-tools@promptbrake
```

Restart Claude Code after installation. This GitHub marketplace is available directly;
an Anthropic directory listing is a separate review.

For other skill-compatible MCP clients, use the standalone instructions below.

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
- “Check my agent does not call send_email without approval.”

[Agent tool-call builder and capture setup](https://promptbrake.com/free-tools/agent-tool-call-checks).

The free tools prepare inputs and artifacts. Response packs require a configured PromptBrake runner and CI access.
Tool-call packs run in the free Action v0.2.0 after staging dispatcher capture is configured. Text comparisons cannot verify backend actions;
release plans are not security certification.

## Public package

Public repository: https://github.com/AJ888/promptbrake-skills

The `promptbrake-free-tools/` directory is the installable skill. The `plugins/` directory bundles those same instructions with the remote MCP
configuration and client manifests. No server implementation is included.
