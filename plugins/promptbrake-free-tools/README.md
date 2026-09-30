# PromptBrake Free Tools plugin

Bundles the PromptBrake remote MCP connection with one skill covering all four
free tools: injection inputs, OWASP LLM risk mappings, AI release planning, and
custom response test packs.

## Use

In Codex CLI:

```sh
codex plugin marketplace add AJ888/promptbrake-skills
codex plugin add promptbrake-free-tools@promptbrake
```

Start a new chat after installation so the skill and tools are picked up.
The package uses the Codex plugin format; it is not a browser extension and is
not installable in every MCP client.

The installer should expose the `promptbrake-free-tools` MCP server at
`https://promptbrake.com/free-tools/mcp` with no authentication, plus the
`promptbrake-free-tools` skill. Approve the connection when your client prompts.
Avoid configuring a second copy of the same MCP connection.

Try: “Build a response test pack for my refund chatbot. It should ask for human
approval before issuing a refund.” The assistant should clarify the exact response
text you want checked before creating the pack.

Tools prepare artifacts. Running tests needs a configured PromptBrake runner and
CI access. Text checks do not establish that backend actions were authorized;
release plans do not certify security. Use test inputs only on authorized systems.
Tool arguments are sent to the hosted service. Inputs and results are not stored
by PromptBrake; operational request metadata is logged. Your assistant has its own
data policies. See https://promptbrake.com/privacy.

## Build from the source repository

Run `python3 scripts/build_free_tools_plugin.py /tmp/promptbrake-free-tools.zip`
from the source repository root. The builder copies the existing skill and examples
into `skills/` in the archive; edit those original files instead of duplicating them.
Only five explicitly selected public files enter the ZIP.

## Publication status

Codex CLI installation and enabled status were verified, and all four live MCP
example calls passed using the installed connection configuration. Natural-language
tool selection in a new chat has not yet been tested. This is a self-published
GitHub marketplace, not an official marketplace approval. The existing
OpenAI submission is separate and remains in review. Do not upload this package
as a replacement for that submission: its package identifier differs. A future
OpenAI update must preserve the existing package identity, include the existing
review materials and branding, and pass the portal checks.

Setup and support: https://promptbrake.com/free-tools and
https://promptbrake.com/contact.
