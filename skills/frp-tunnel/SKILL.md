---
name: frp-tunnel
description: "High-performance reverse proxy for NAT traversal: expose local TCP/UDP/HTTP services to public domains via frps/frpc tunnels."
---

# FRP Tunnel (`/frp-tunnel`)

Высокоскоростной реверс-прокси для проброса локальных сервисов через NAT и фаерволы на публичные IP/домены.

## Локальный клиент:
`/opt/homebrew/bin/frpc`

## Конфигурация клиента (`frpc.toml`):
```toml
serverAddr = "vps.example.com"
serverPort = 7000

[[proxies]]
name = "web-preview"
type = "http"
localIP = "127.0.0.1"
localPort = 3000
customDomains = ["preview.example.com"]

[[proxies]]
name = "api-gateway"
type = "tcp"
localIP = "127.0.0.1"
localPort = 8787
remotePort = 8787
```

## Запуск:
```bash
frpc -c /path/to/frpc.toml
```
