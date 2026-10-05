# PromptBrake Free Tools plugin

Bundles the PromptBrake remote MCP connection with one skill covering the
free tools: injection inputs, OWASP LLM risk mappings, AI release planning, and
custom response test packs and agent tool-call test packs.

## Use

In Codex CLI:

```sh
codex plugin marketplace add AJ888/promptbrake-skills
codex plugin add promptbrake-free-tools@promptbrake
```

Start a new chat after installation so the skill and tools are picked up.
For Claude Code:

```sh
claude plugin marketplace add AJ888/promptbrake-skills
claude plugin install promptbrake-free-tools@promptbrake
```

Restart Claude Code after installation. The package includes Codex, Claude Code, and Cursor
plugin manifests; other MCP clients may need a separate connection.

The installer should expose the `promptbrake-free-tools` MCP server at
`https://promptbrake.com/free-tools/mcp` with no authentication, plus the
`promptbrake-free-tools` skill. Approve the connection when your client prompts.
Avoid configuring a second copy of the same MCP connection.

## Try this first

After connecting PromptBrake, copy one prompt into your assistant. It may ask a
few questions before calling the matching tool.

### Prompt-injection test inputs

```text
Help me prepare prompt-injection tests for my customer-support chatbot.
```

Get fixed adversarial inputs to try on a chatbot you own or are authorized to test. No CI access is needed to generate them; the tool does not run them against your chatbot.

### Refund chatbot response checks

```text
Help me build response checks for a refund bot that should ask for human approval.
```

Get a tests.json pack after choosing the exact response text to check. Creating it is free; running it requires a configured PromptBrake runner and CI access. Text checks do not verify whether a refund was actually authorized.

### AI agent release plan

```text
Help me plan my AI agent’s release. Ask me what you need to know.
```

Get planning gaps and a starter gate policy based on your answers. No CI access is needed to create the plan. It does not execute tests or certify release readiness.

Tools prepare artifacts. Running tests needs a configured PromptBrake runner and
CI access. Text checks do not establish that backend actions were authorized;
release plans do not certify security. Use test inputs only on authorized systems.
Tool arguments are sent to the hosted service. Inputs and results are not stored
by PromptBrake; operational request metadata is logged. Your assistant has its own
data policies. See [Privacy policy](https://promptbrake.com/privacy).

## Build from the source repository

Run `python3 scripts/build_free_tools_plugin.py /tmp/promptbrake-free-tools.zip`
from the source repository root. The builder copies the existing skill and examples
into `skills/` in the archive; edit those original files instead of duplicating them.
Only nine explicitly selected public files enter the ZIP.

The plugin files and bundled skill instructions are licensed under MIT. This
license does not cover the hosted service or PromptBrake's private server code.

## Publication status

Codex CLI installation and enabled status were verified, and all four live MCP
example calls passed using the installed connection configuration. The refund release-planning workflow also invoked the MCP tool from a natural-language
request in Codex. This is a self-published
GitHub marketplace, not an official marketplace approval. The existing
OpenAI submission is separate and remains in review. Do not upload this package
as a replacement for that submission: its package identifier differs. A future
OpenAI update must preserve the existing package identity, include the existing
review materials and branding, and pass the portal checks.

Setup and support: https://promptbrake.com/free-tools and
https://promptbrake.com/contact.

## Cursor

The repository includes `.cursor-plugin/marketplace.json` and a Cursor manifest
that reuses the bundled skill and `.mcp.json`. No API key is required.
Cursor Marketplace application submitted on 2026-09-29; awaiting review as of
2026-09-30. Submission is not marketplace publication.
For local testing, place the complete built plugin under
`~/.cursor/plugins/local/promptbrake-free-tools/`, then restart Cursor and check
that the skill and MCP server appear. Avoid adding a duplicate MCP connection.

## Agent tool-call checks

Ask: “Build a test pack that checks my agent does not call send_email for an unapproved request.”

The fifth tool, `build_agent_tool_tests`, prepares the pack. Run it with
[PromptBrake Action v0.2.0](https://github.com/AJ888/promptbrake-action/releases/tag/v0.2.0)
and one-time staging dispatcher capture. Missing or incomplete capture cannot pass.
It checks dispatched tool names and configured arguments, not successful backend effects.
A licensed local runner adds retained history, comparisons, gates and exports.

[Build a pack and configure capture](https://promptbrake.com/free-tools/agent-tool-call-checks).
