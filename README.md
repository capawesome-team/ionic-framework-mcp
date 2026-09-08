# Ionic Framework MCP Server

Unofficial MCP server for the official [Ionic Framework](https://ionicframework.com) documentation. It gives AI assistants the current documentation for Ionic Framework v9 and v8 — including the component API reference and the usage examples for Angular, React, Vue and vanilla JavaScript — plus the Ionic blog. Not affiliated with or endorsed by Ionic or OutSystems.

Maintained by [Capawesome](https://capawesome.io).

## Endpoint

The server is hosted and ready to use. No account, no token, no installation:

https://ionic-framework-mcp.capawesome.io/mcp

```
https://ionic-framework-mcp.capawesome.io/mcp
```

## Installation

### Claude Code

```bash
claude mcp add --transport http ionic-framework https://ionic-framework-mcp.capawesome.io/mcp
```

### Claude Desktop / Claude.ai

Go to **Settings → Connectors → Add custom connector** and enter:

- **Name**: `Ionic Framework`
- **URL**: `https://ionic-framework-mcp.capawesome.io/mcp`

### Cursor

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](cursor://anysphere.cursor-deeplink/mcp/install?name=ionic-framework&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vaW9uaWMtZnJhbWV3b3JrLW1jcC5jYXBhd2Vzb21lLmlvL21jcCJ9)

Or add `.cursor/mcp.json` to your project:

```json
{
  "mcpServers": {
    "ionic-framework": {
      "url": "https://ionic-framework-mcp.capawesome.io/mcp"
    }
  }
}
```

### VS Code

[Install in VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=ionic-framework&config=%7B%22name%22%3A%22ionic-framework%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fionic-framework-mcp.capawesome.io%2Fmcp%22%7D)

Or add `.vscode/mcp.json` to your project:

```json
{
  "servers": {
    "ionic-framework": {
      "type": "http",
      "url": "https://ionic-framework-mcp.capawesome.io/mcp"
    }
  }
}
```

### Windsurf

Add the server to `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "ionic-framework": {
      "serverUrl": "https://ionic-framework-mcp.capawesome.io/mcp"
    }
  }
}
```

### Zed

Add the server to your Zed `settings.json`:

```json
{
  "context_servers": {
    "ionic-framework": {
      "url": "https://ionic-framework-mcp.capawesome.io/mcp"
    }
  }
}
```

### Any client via npx

Clients that cannot connect to a remote server over HTTP can run this package, which proxies stdio to the hosted server:

```json
{
  "mcpServers": {
    "ionic-framework": {
      "command": "npx",
      "args": ["-y", "@capawesome/ionic-framework-mcp"]
    }
  }
}
```

Requires Node.js 22 or later.

## Tools

| Tool                  | Purpose                                                                           | Parameters                                                |
| --------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------- |
| `search_docs`         | Search the documentation by keyword. Start here for any Ionic Framework question. | `query` (required), `section`, `version`, `limit`         |
| `get_doc_page`        | Read a full documentation page returned by `search_docs`.                         | `url` (required), `version`                               |
| `list_components`     | List Ionic Framework components with their API reference.                         | `query`, `version`, `limit`                               |
| `get_component_usage` | Read usage examples for a component, per framework.                               | `component` (required), `example`, `framework`, `version` |
| `list_blog_posts`     | List recent posts from the Ionic blog.                                            | —                                                         |

## Versions

The documentation is available for Ionic Framework **v9** (default) and **v8**. Pass the `version` parameter to target a specific version.

## Rate limits

The endpoint is limited to **100 requests per minute per IP**. Requests over the limit are answered with `429 Too Many Requests`; retry after a short wait.

## Privacy

Your IP address is processed for rate limiting only. Queries and tool arguments are not stored, not logged beyond Cloudflare's standard edge logs, and never used for training.

## Related

- [Capacitor MCP Server](https://github.com/capawesome-team/capacitor-mcp) — the same for the Capacitor documentation, plugin list and blog.
- [Capawesome MCP Server](https://github.com/capawesome-team/mcp) — the official MCP server for the Capawesome documentation and the Capawesome Cloud management API.
- [Capawesome Cloud Live Updates](https://capawesome.io/cloud/live-updates/) — ship JavaScript, HTML and CSS changes to your app without an app store review.
- [Capawesome Cloud Native Builds](https://capawesome.io/cloud/native-builds/) — build native iOS and Android apps in the cloud, without a Mac.
- [Capawesome Cloud App Store Publishing](https://capawesome.io/cloud/app-store-publishing/) — submit builds to the Apple App Store and Google Play Store.

## Attribution

The documentation content is © the Ionic team, licensed under [Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0) and sourced from [`ionic-team/ionic-docs`](https://github.com/ionic-team/ionic-docs). It is converted from MDX to Markdown for delivery over MCP and otherwise served unmodified in substance. The component API reference comes from the [`@ionic/docs`](https://www.npmjs.com/package/@ionic/docs) package (MIT). Blog excerpts come from the [Ionic blog](https://ionic.io/blog) and link to the original post.

See [NOTICE](NOTICE) for the full attribution.

## Development

```bash
npm install
npm run build
npm test
```

Set `IONIC_FRAMEWORK_MCP_URL` to point the proxy at a local server instead of the hosted one:

```bash
IONIC_FRAMEWORK_MCP_URL=http://localhost:8787/mcp node dist/index.js
```

## Release

Releases are managed by [release-please](https://github.com/googleapis/release-please). Merging its release pull request tags the version, publishes the package to npm and then publishes `server.json` to the [MCP Registry](https://registry.modelcontextprotocol.io). The version in `server.json` is bumped by release-please together with `package.json`, so it never has to be edited by hand. To publish to the registry manually, install [`mcp-publisher`](https://github.com/modelcontextprotocol/registry), run `mcp-publisher login dns --domain=capawesome.io --private-key=<key>` with the Ed25519 private key from the password manager and then `mcp-publisher publish`.

## License

See [LICENSE](LICENSE).
