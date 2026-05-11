# claude-beats

KawaiiLLM 的 Claude Code 插件 marketplace。

## 使用

在 Claude Code 里:

```
/plugin marketplace add KawaiiLLM/claude-beats
```

然后浏览或安装具体插件:

```
/plugin install <plugin-name>@claude-beats
```

## 当前 plugins

| Plugin | Version | Repo | 用途 |
|---|---|---|---|
| `bilibili-mcp` | 0.3.0 | [KawaiiLLM/bilibili_mcp](https://github.com/KawaiiLLM/bilibili_mcp) | Bilibili MCP Server,CookieCloud 登录 + 完整反爬基线 |

## 添加新插件

在 `.claude-plugin/marketplace.json` 的 `plugins` 数组里追加:

```json
{
  "name": "<plugin-id>",
  "source": {
    "source": "github",
    "repo": "KawaiiLLM/<repo-name>"
  },
  "version": "<x.y.z>",
  "description": "...",
  "strict": false,
  "mcpServers": {
    "<server-id>": {
      "command": "node",
      "args": ["${CLAUDE_PLUGIN_ROOT}/dist/cli.js", "stdio"]
    }
  }
}
```

target 仓库需要满足:
- 可被 Claude Code clone(public 或配置过 SSH key)
- 包含 `command` 引用的可执行文件(预编译 dist 或 binary)
- 若有 env vars 依赖,在 plugin README 里说明,Claude Code 不会代为配置

## License

GPL-3.0-only(继承单个 plugin 的许可;marketplace 本身只是描述符)
