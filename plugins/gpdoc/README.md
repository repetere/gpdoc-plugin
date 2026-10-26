# GPDoc plugin for Codex and Claude Code

The GPDoc plugin opens the graphical GPEditor from Codex and Claude Code. You can edit Markdown and GPDoc files, save exact revisions, and share through your GPDoc account. Local file tools are limited to the workspace opened in the client.

## Requirements

- Node.js 22 or later
- Codex or Claude Code with plugin and MCP support
- A GPDoc account only when sharing

No dependency installation is required inside the plugin.

## Codex

Add this repository as a local marketplace, then install `gpdoc@gpdoc`:

```bash
codex plugin marketplace add /path/to/gpdoc
codex plugin add gpdoc@gpdoc
```

Restart Codex after installation so the bundled MCP server, editor app, and skill load from the plugin cache.

## Claude Code

Add this repository as a marketplace and install the plugin:

```bash
claude plugin marketplace add /path/to/gpdoc
claude plugin install gpdoc@gpdoc
```

For a temporary development session:

```bash
claude --plugin-dir ./plugins/gpdoc
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

## Shared editor in 0.4.0

Claude Code Desktop Preview and Codex use one GPEditor frontend. It includes exports (PDF, DOCX, HTML, Markdown and LaTeX), export progress and saved-file actions, themes and variables, image editing, HTML preview, file details, account settings, sharing, provider/cloud storage, publishing, and collaboration controls. Remote services require the corresponding signed-in accounts. Local exports do not require MCP network services.

Ask Claude to open a .md or .markdown file in GPEditor, or use `/gpdoc:open path/to/document.md`. The plugin skill and session context prefer GPEditor for interactive document opening. Open its returned local URL in Claude Desktop Preview. Claude controls its built-in file pane and file-path clicks; this plugin cannot replace that viewer. Terminal users can open the returned local URL in a browser.

Drafts connect automatically for chat inspection, comments and suggestions. A visible control disconnects them. Reviews stay in the draft until the user saves. The same revision checks protect saves in both clients.

The source build checks frontend script identity and records `mcp/editor-parity.json`. Native and hosted ChatGPT packages have separate versions. Anthropic directory review is separate from this public marketplace release. Live native-host and signed-in provider acceptance remain separate from automated browser/protocol checks.
