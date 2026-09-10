# Assembly Recognition

Assembly Recognition by Quantum Workplace brings employee recognition workflows to your AI assistant
through Assembly's hosted MCP server and two end-user skills. It works in Claude and the ChatGPT desktop app.
See the [marketplace README](../../README.md) for installation steps.

## What you can do

- Review recognition opportunities for your direct reports.
- Find upcoming team birthdays and work anniversaries.
- Look up coworkers and groups before drafting recognition.
- Check available points, recognition currency, and core values.
- Draft specific, evidence-based recognition messages.
- Preview the exact recipients, message, points, core value, and privacy setting before posting.

The plugin is intended for employees and managers using an HR and recognition platform. It is not a
coding or software-development assistant.

## Skills

| Skill | Use it when |
| --- | --- |
| `craft-recognition` | You want to recognize, thank, or celebrate a specific coworker and need help drafting and posting it. |
| `review-my-team` | You manage people and want a brief on whom to recognize this week, with evidence-backed drafts. |

## Connection

The plugin connects to the hosted Assembly MCP server at `https://mcp.joinassembly.com/mcp`. Your
assistant asks you to sign in and authorize your Assembly account when a skill or tool needs access.
Sign-in uses standard OAuth with PKCE. No API keys or local software are required.

## Permissions and safety

Assembly keeps read and recognition-write access separate. Existing workspace membership, roles,
report relationships, profile visibility, recipient eligibility, allowance, and recognition settings
continue to apply.

Posting recognition uses a two-step flow: the tool first returns an exact preview without creating a
post, and a confirmed call is allowed only after explicit user approval.

Tool results use documented public fields rather than raw service responses. The package contains
only plugin manifests, the remote MCP connection, this guide, and end-user skills.
