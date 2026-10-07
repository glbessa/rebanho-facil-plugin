# Plugin Rebanho Fácil

Catálogo de plugins do Rebanho Fácil para Claude, ChatGPT e Codex. O plugin
fica em [`plugins/rebanho-facil`](plugins/rebanho-facil); o README dele explica
o que faz, quais dados usa e como instalar.

| Arquivo | Quem lê |
|---|---|
| `.claude-plugin/marketplace.json` | Claude Code |
| `.agents/plugins/marketplace.json` | Codex / ChatGPT |
| `plugins/rebanho-facil/.claude-plugin/plugin.json`, `.mcp.json` | Claude |
| `plugins/rebanho-facil/plugin.json`, `mcp.json` | ChatGPT e Codex |
| `plugins/rebanho-facil/skills/` | os dois |

As tools vêm do servidor MCP do Rebanho Fácil. Ao renomear uma tool lá,
atualize a skill aqui e suba `version` nos dois `plugin.json`.

Licença MIT.
