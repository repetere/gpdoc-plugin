# GPDoc plugin marketplace

This repository publishes the GPDoc plugin for Codex and Claude Code. Claude Code and Codex use the same GPEditor frontend for Markdown editing, exports, themes, review, account and service actions. Workspace saves remain revision-checked. Sharing and publishing require explicit user actions.

## Install in Claude Code

```bash
claude plugin marketplace add repetere/gpdoc-plugin
claude plugin install gpdoc@gpdoc
```

The Anthropic directory listing is a separate submission and requires approval. Installation from this public marketplace is available now.

After installation, restart Claude and use `/gpdoc:open path/to/document.md`, or ask Claude to open the document in GPEditor. Claude controls its built-in file-link viewer; interactive open requests use the GPEditor Browser/Preview flow.

## Install in Codex

```bash
git clone https://github.com/repetere/gpdoc-plugin.git
codex plugin marketplace add ./gpdoc-plugin
codex plugin add gpdoc@gpdoc
```

Restart the client after installation so the bundled local MCP server, GPEditor application, and GPDoc skill load from the plugin cache.

## Package

The distributable plugin is in [`plugins/gpdoc`](plugins/gpdoc). It includes separate Codex and Claude Code manifests, one shared skill, a workspace-scoped MCP server, and the GPEditor bundle.

See the [plugin README](plugins/gpdoc/README.md) for usage, authentication, and environment configuration.

## Privacy and support

- Privacy policy: https://gpdoc.io/privacy
- Terms: https://gpdoc.io/terms
- Support: support@gpdoc.io

This package is proprietary software. See [`LICENSE`](LICENSE).
