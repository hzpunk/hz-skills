---
name: nuclei-secops
description: "Fast, template-based vulnerability scanning and web AppSec testing using Nuclei: CVEs, misconfigurations, exposed panels, and automated pentesting."
---

# Nuclei SecOps (`/nuclei-secops`)

Быстрое шаблонное сканирование уязвимостей, конфигурационных ошибок и открытых панелей с помощью Nuclei (ProjectDiscovery).

## Локальный бинарник:
`/opt/homebrew/bin/nuclei`

## Основные команды аудита:
```bash
# 1. Быстрый аудит сайта на критические CVE и утечки конфигов (.env, git)
nuclei -u https://example.com -tags cve,exposure,misconfig -severity critical,high

# 2. Проверка открытых админок и панелей управления
nuclei -u https://example.com -tags panel,login

# 3. Аудит SSL/TLS сертификатов и заголовков безопасности (HSTS, CSP, X-Frame)
nuclei -u https://example.com -tags ssl,headers

# 4. JSON-отчет для CI/CD контура
nuclei -u https://example.com -json-export /tmp/nuclei-report.json
```

## Инвариант безопасности:
Запрещено запускать агрессивные DoS/Bruteforce шаблоны на боевых продакшн-серверах без предварительного согласования с CISO.
