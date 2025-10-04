# 🔍 Shodan Cheatsheet

Este repositório é um guia de uso do Shodan — tanto via interface web quanto pela linha de comando (CLI) com a API oficial.

> Ideal para profissionais de segurança, pentesters, analistas de GRC, auditores e entusiastas.

## 📦 Instalação da CLI do Shodan

### 1. Instale o pacote via pip:
```bash
pip install shodan
```

### 2. Obtenha sua API Key:
Acesse: https://account.shodan.io

### 3. Configure a CLI:
```bash
shodan init SUA_API_KEY
```

## 🌐 Comandos via Interface Web (shodan.io)

| Objetivo                                   | Comando de Busca                                |
|-------------------------------------------|-------------------------------------------------|
| Câmeras abertas com screenshot            | `has_screenshot:true`                           |
| RDP sem autenticação no Brasil            | `port:3389 country:BR`                          |
| Dispositivos com Windows 7 expostos       | `os:"Windows 7"`                                |
| Firewalls SonicWall expostos              | `product:"SonicWALL" port:443`                  |
| Buscar por CVE específica                 | `vuln:CVE-2020-0601`                            |
| Routers MikroTik com Winbox exposto       | `mikrotik port:8291`                            |
| Webcams sem autenticação                  | `netcam`                                        |
| Servidores FTP abertos                    | `port:21 Anonymous user logged in`              |
| Dispositivos IoT da TP-Link               | `tplink` ou `TP-LINK`                           |

## 💻 Exemplos via CLI (Terminal)

> Requer CLI configurada com API (veja a instalação acima)

### Buscar servidores Apache no Brasil:
```bash
shodan search "apache country:BR" --fields ip_str,port,org --limit 20
```

### Encontrar máquinas Windows 7 vulneráveis:
```bash
shodan search "os:Windows 7 country:BR" --fields ip_str,port,org,product,version,vulns --limit 20
```

### Obter info detalhada de um IP:
```bash
shodan host 187.45.24.166
```

### Buscar dispositivos MikroTik com vulnerabilidade:
```bash
shodan search "mikrotik" --fields ip_str,port,vulns --limit 50
```

### Exportar resultado para CSV:
```bash
shodan search "os:Windows 7 country:BR" --fields ip_str,port,org,product,version,vulns --limit 100 > resultado.csv
```

## 📁 Sugestão de estrutura do Git
```
📁 shodan-ultimate-cheatsheet
├── README.md
├── cli-queries.md
├── web-queries.md
├── shodan-install.md
```

Feito com 💻 por [Douglas Lockshield](https://github.com/DougLockshield)
