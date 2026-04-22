# Bitrix24 Task MCP – Lokaler Start

Dieses Repo ist als **task-first Fork** gedacht. Standardmäßig werden nur die relevanten Task-/Projekt-/User-Tools geladen.

## 1) Installation

```bash
cd ~/bitrix24-mcp-server
npm install
```

## 2) Konfiguration

Lege eine `.env` an:

```env
BITRIX24_WEBHOOK_URL=https://b24-nnfdt0.bitrix24.ae/rest/1/ygo28wfvn1u6wiji/
BITRIX24_MODE=tasks
NODE_ENV=development
LOG_LEVEL=info
```

## 3) Build

```bash
npm run build
```

## 4) Start als MCP-Server

```bash
node build/index.js
```

### Erwartetes Verhalten
- `BITRIX24_MODE=tasks` → task-first Toolset
- `BITRIX24_MODE=full` → kompletter CRM-Umfang

## 5) Claude Desktop / MCP-Client Eintrag

```json
{
  "mcpServers": {
    "bitrix24": {
      "command": "node",
      "args": ["/Users/openclaw/bitrix24-mcp-server/build/index.js"],
      "env": {
        "BITRIX24_WEBHOOK_URL": "https://b24-nnfdt0.bitrix24.ae/rest/1/ygo28wfvn1u6wiji/",
        "BITRIX24_MODE": "tasks"
      }
    }
  }
}
```

## 6) Schnelltest

Wenn der Server läuft, sollten diese Tools sichtbar sein:
- `bitrix24_create_task`
- `bitrix24_get_task`
- `bitrix24_list_tasks`
- `bitrix24_update_task`
- `bitrix24_create_project`
- `bitrix24_list_projects`
- `bitrix24_get_project`
- `bitrix24_get_user`
- `bitrix24_get_all_users`
- `bitrix24_resolve_user_names`
- `bitrix24_validate_webhook`
- `bitrix24_diagnose_permissions`
- `bitrix24_check_crm_settings`

## 7) Full Mode

Wenn du später den kompletten Bitrix24-Umfang brauchst:

```bash
BITRIX24_MODE=full node build/index.js
```

Oder im MCP-Client in den Env-Variablen setzen.
