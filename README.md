# Assembly Recognition Plugin

This repository contains the Assembly Recognition plugin for ChatGPT and Claude. IT administrators
can import the included marketplace manifest from GitHub to distribute the plugin in ChatGPT, or
reference this repository from a private or internal marketplace to distribute it in Claude. See
[Deploy to ChatGPT](#deploy-to-chatgpt) and [Deploy to Claude](#deploy-to-claude).

| Plugin | What employees can do with it |
| --- | --- |
| [Assembly Recognition](plugins/assembly-recognition/) | Recognize coworkers with [Assembly](https://joinassembly.com/): find recognition opportunities, draft evidence-based messages, and post recognition after confirming a preview. |

The plugin connects to Assembly's hosted MCP server at `https://mcp.joinassembly.com/mcp`. Nothing is
installed on employee devices beyond the assistant itself. Each employee signs in to their own Assembly
account the first time the plugin needs access, and Assembly's existing permissions, roles, and
recognition settings continue to apply.

**This is a beta program.** If you run into problems or have questions, reply to the beta program email
you received from Assembly. That thread reaches the team supporting this rollout.

## Before you begin

- **Repository access.** This repository is public. No GitHub invitation is needed to access the
  plugin. For an internal marketplace, use a GitHub account that can access your company's
  marketplace repository.
- **Assembly accounts.** Employees need active Assembly accounts. No API keys or shared credentials
  are required. Each employee signs in to Assembly the first time the plugin needs access.

## Deploy to Claude

Claude requires a private or internal GitHub repository for your company's organization marketplace.
This repository supplies the plugin. Your company's repository supplies the Claude marketplace catalog.

In `.claude-plugin/marketplace.json` in your company's repository, add the plugin using this
reference:

```json
{
  "name": "company-plugins",
  "owner": { "name": "Your company" },
  "plugins": [
    {
      "name": "assembly-recognition",
      "source": {
        "source": "git-subdir",
        "url": "https://github.com/joinassembly/mcp.git",
        "path": "plugins/assembly-recognition"
      }
    }
  ]
}
```

For an existing catalog, add only the plugin entry. Claude fetches the plugin directly from this
public repository; your company's marketplace repository stays private or internal.

1. Have a Team/Enterprise Owner or Primary Owner enable Cowork and Skills and install the Claude
   GitHub App on the internal repository.
2. Open **Organization settings > Plugins > Add plugins > GitHub** and enter your internal
   repository as `your-company/your-marketplace`.
3. After syncing, set Assembly Recognition to **Installed by default** or **Available for install**.

To pick up a new release, select **Update**. Upstream changes alone do not change your internal
repository.

See [Claude's organization plugin guide](https://support.claude.com/en/articles/13837433-manage-plugins-for-your-organization).

## Deploy to ChatGPT

Import the marketplace manifest included in this repository:

1. In ChatGPT, open **Admin > Plugins > Add > Import marketplace**.
2. Enter `https://github.com/joinassembly/mcp` as **Source**. Leave **Path** empty and authorize
   GitHub access when prompted.
3. Review the import results and configure Assembly Recognition's installation policy for your team.

Use **Sync now** on the imported marketplace to request an update.

See [OpenAI's plugin management guide](https://learn.chatgpt.com/docs/enterprise/plugin-management)
for import, access, and sync details. This MCP-based plugin requires the ChatGPT desktop app.

### Use an existing internal ChatGPT marketplace

If your company already maintains a marketplace, you can reference the plugin from its catalog.
Add this entry to the `plugins` array in your internal repository's
`.agents/plugins/marketplace.json`:

```json
{
  "name": "assembly-recognition",
  "source": {
    "source": "git-subdir",
    "url": "https://github.com/joinassembly/mcp.git",
    "path": "./plugins/assembly-recognition"
  },
  "category": "Productivity"
}
```

This references the plugin directly from this public GitHub repository. The importing admin's GitHub
account needs access to your internal marketplace repository.

Import your internal marketplace's repository URL instead of this repository, or use **Sync now** if
it is already connected to ChatGPT.

## Verify the rollout

Ask an employee to find Assembly Recognition in their assistant's installed plugins.
Their first request that needs Assembly access prompts them to sign in to their Assembly account.

## Removing the plugin

For ChatGPT, manage Assembly Recognition's availability under **Admin > Plugins**. Removing its
catalog entry alone does not delete the imported workspace copy.

For Claude, set Assembly Recognition to **Not available** under **Organization settings > Plugins**.

Removing the plugin does not affect Assembly accounts or data. Employees can also revoke the
assistant's access from their Assembly account settings.

## License

This repository is proprietary to Quantum Workplace. See [LICENSE](LICENSE).

## Releases

Each release bumps the version in both plugin manifests under `plugins/assembly-recognition/` and is
recorded in [CHANGELOG.md](CHANGELOG.md). Use **Sync now** in ChatGPT or **Update** in Claude to
pick up new releases as we publish them.
