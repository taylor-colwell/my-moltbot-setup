---
name: ccc-mcp-server
description: Manage the Elisity CCC (Cloud Control Center) MCP server hosted on taylor-mcp-host VM. Use when starting, stopping, troubleshooting, or configuring the CCC API MCP server, or when setting up Claude Code to connect to it.
---

# Elisity CCC MCP Server

## Overview

The CCC MCP server provides Claude with access to the Elisity Cloud Control Center API for microsegmentation workflows. It's hosted on the `taylor-mcp-host` VM and exposes tools for managing Policy Groups, Policy Sets, Virtual Edges, IdentityGraph, and other CCC resources.

---

## Server Details

| Property | Value |
|----------|-------|
| **VM Hostname** | taylor-mcp-host |
| **Local IP** | 10.100.102.98 |
| **Tailscale IP** | 100.80.139.8 |
| **Port** | 3001 |
| **SSE Endpoint** | http://<IP>:3001/sse |
| **Config UI** | http://<IP>:3001/settings.html |
| **Health Check** | http://<IP>:3001/health |

### VM Access Credentials

```
Host: 10.100.102.98 (or 100.80.139.8 via Tailscale)
Username: taylor
Password: tjcolwell
```

---

## Starting the Server

### Manual Start

SSH into the VM and start the server:

```bash
ssh taylor@10.100.102.98
cd /home/taylor/ccc-mcp
npm run start:web
```

Or run in background:

```bash
ssh taylor@10.100.102.98 "cd /home/taylor/ccc-mcp && nohup npm run start:web > /tmp/mcp.log 2>&1 &"
```

### Using sshpass (non-interactive)

```bash
sshpass -p 'tjcolwell' ssh taylor@10.100.102.98 "cd /home/taylor/ccc-mcp && nohup npm run start:web > /tmp/mcp.log 2>&1 &"
```

---

## Systemd Service Setup (Auto-start on Boot)

### 1. Create the service file

SSH into the VM and create `/etc/systemd/system/ccc-mcp.service`:

```bash
sudo tee /etc/systemd/system/ccc-mcp.service << 'EOF'
[Unit]
Description=Elisity CCC MCP Server
After=network.target

[Service]
Type=simple
User=taylor
WorkingDirectory=/home/taylor/ccc-mcp
ExecStart=/usr/bin/node /home/taylor/ccc-mcp/build/index.js --transport=web
Restart=on-failure
RestartSec=10
Environment=NODE_ENV=production

[Install]
WantedBy=multi-user.target
EOF
```

### 2. Enable and start the service

```bash
sudo systemctl daemon-reload
sudo systemctl enable ccc-mcp
sudo systemctl start ccc-mcp
```

### 3. Service management commands

```bash
# Check status
sudo systemctl status ccc-mcp

# View logs
sudo journalctl -u ccc-mcp -f

# Restart
sudo systemctl restart ccc-mcp

# Stop
sudo systemctl stop ccc-mcp
```

---

## Claude Code Configuration

Add the following to `~/.claude/settings.json` under `mcpServers`:

### Using Local Network IP

```json
{
  "mcpServers": {
    "ccc-mcp": {
      "type": "http",
      "url": "http://10.100.102.98:3001/sse"
    }
  }
}
```

### Using Tailscale IP (recommended for remote access)

```json
{
  "mcpServers": {
    "ccc-mcp": {
      "type": "http",
      "url": "http://100.80.139.8:3001/sse"
    }
  }
}
```

After updating settings.json, restart Claude Code for changes to take effect.

---

## Configuring CCC API Credentials

### Option 1: Via Web UI

Navigate to `http://10.100.102.98:3001/settings.html` and update:
- API Base URL
- OAuth Client ID
- OAuth Client Secret

### Option 2: Via .env file

Edit `/home/taylor/ccc-mcp/.env` on the VM:

```bash
# API Configuration
API_BASE_URL=https://your-ccc-instance.elisity.io

# OAuth2 Client Credentials
OAUTH_CLIENT_ID=your_client_id
OAUTH_CLIENT_SECRET=your_client_secret
OAUTH_SCOPES=openid
```

Restart the server after editing.

---

## Troubleshooting

### Server won't start

1. Check if port 3001 is in use:
   ```bash
   sudo lsof -i :3001
   ```

2. Check logs:
   ```bash
   cat /tmp/mcp.log
   # or if using systemd:
   sudo journalctl -u ccc-mcp -n 50
   ```

3. Verify node is installed:
   ```bash
   node --version  # Should be >= 20.0.0
   ```

### Can't connect from Claude Code

1. **Check server is running:**
   ```bash
   curl http://10.100.102.98:3001/health
   ```

2. **Check network connectivity:**
   - If on same network, use local IP: 10.100.102.98
   - If remote, use Tailscale IP: 100.80.139.8
   - Ensure Tailscale is connected on both machines

3. **Check firewall:**
   ```bash
   sudo ufw status
   sudo ufw allow 3001/tcp  # if needed
   ```

### Authentication errors with CCC API

1. Verify credentials in `.env` or via the Config UI
2. Test connection via Config UI at `/settings.html`
3. Check if OAuth token is expired (server auto-refreshes, but restart may help)

### Server crashes or becomes unresponsive

1. Check memory/CPU on VM:
   ```bash
   htop
   ```

2. Restart the service:
   ```bash
   sudo systemctl restart ccc-mcp
   ```

---

## Available MCP Tools

The server exposes tools for the Elisity Gateway API including:

- **Identity Graph**: OUI mappings, time-based access configurations
- **Policy Management**: Policy Groups, Policy Sets, Policy Group Labels
- **Infrastructure**: Virtual Edges, Virtual Edge Nodes, Site Labels, Distribution Zones
- **Discovery**: Asset discovery, endpoint management

Use the MCP tools to automate CCC workflows directly from Claude Code.
