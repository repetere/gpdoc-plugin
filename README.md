# GPDoc plugin marketplace

This repository publishes the GPDoc plugin for Codex and Claude Code. The plugin opens GPEditor for workspace-scoped Markdown editing, preserves GPDoc review metadata, and shares a saved file only when the user explicitly requests it.

## Install in Claude Code

```bash
claude plugin marketplace add repetere/gpdoc-plugin
claude plugin install gpdoc@gpdoc
```

After Anthropic approves the community-directory submission, GPDoc will also be available from the `claude-community` marketplace.

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
