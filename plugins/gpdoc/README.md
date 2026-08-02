# GPDoc plugin for Codex and Claude Code

The GPDoc plugin opens the graphical GPEditor from Codex and Claude Code. You can edit Markdown and GPDoc files, save exact revisions, and share through your GPDoc account. Local file tools are limited to the workspace opened in the client.

## Requirements

- Node.js 20 or later
- Codex or Claude Code with plugin and MCP support
- A GPDoc account only when sharing

No dependency installation is required inside the plugin.

## Codex

Clone the public marketplace, then install `gpdoc@gpdoc`:

```bash
git clone https://github.com/repetere/gpdoc-plugin.git
codex plugin marketplace add ./gpdoc-plugin
codex plugin add gpdoc@gpdoc
```

Restart Codex after installation so the bundled MCP server, editor app, and skill load from the plugin cache.

## Claude Code

Add the public marketplace and install the plugin:

```bash
claude plugin marketplace add repetere/gpdoc-plugin
claude plugin install gpdoc@gpdoc
```

For a temporary development session:

```bash
claude --plugin-dir ./gpdoc-plugin/plugins/gpdoc
```

## Use

In Codex, ask:

```text
Open README.md in GPEditor.
```

Codex calls `gpdoc_open_editor` and renders GPEditor in the conversation as an MCP App.

In Claude Code Desktop, ask:

```text
Open README.md in GPEditor.
```

Claude calls `gpdoc_open_editor` and returns a local preview URL. Open that URL in Claude's Preview pane. The URL is short-lived and can access only the requested file.

You can also ask either client to edit through tools without opening the graphical editor. GPDoc-managed documents use review suggestions by default. Plain Markdown is edited directly without adding GPDoc metadata.

Ask the client to share only when you want a remote GPDoc link. The plugin will start device login if needed and will show a verification URL and code. Tokens stay in the MCP server process and are not returned to the model.

## Optional environment configuration

- `GPDOC_ACCESS_TOKEN`: controlled noninteractive authentication
- `GPDOC_API_BASE_URL`: GPDoc API override
- `GPDOC_AUTH0_DOMAIN`, `GPDOC_AUTH0_CLIENT_ID`, `GPDOC_AUTH0_AUDIENCE`: public Auth0 configuration overrides
- `GPDOC_ALLOW_DEVELOPMENT_ENDPOINTS=true`: allow loopback development endpoints

Do not place access tokens in tracked files.
