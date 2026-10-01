<h1 align="center">
  <img src="https://raw.githubusercontent.com/MoZoHuJa/OS/main/docs/scarlixos-banner.png" alt="ScarLiXoS v19 — Sovereign AI Cloud" width="100%" />
</h1>

<p align="center">
  <strong>ScarLiXoS v19</strong> — Suverénny domáci OS pre AI cloud, coding, gaming a rodinnú zábavu.<br/>
  Architektúra Secure Host-Bridge · Token autentifikácia · 4-tier AI failover · EndeavourOS (Arch) base
</p>

<p align="center">
  <a href="https://github.com/MoZoHuJa/OS/releases/tag/v19.0.2"><img alt="Version" src="https://img.shields.io/badge/version-v19.0.2-10b981?style=flat-square" /></a>
  <a href="https://github.com/MoZoHuJa/OS"><img alt="Repo" src="https://img.shields.io/badge/repo-MoZoHuJa%2FOS-06b6d4?style=flat-square" /></a>
  <a href="https://github.com/MoZoHuJa/OS/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/badge/license-MIT-14b8a6?style=flat-square" /></a>
  <a href="https://github.com/MoZoHuJa/OS/actions"><img alt="CI" src="https://img.shields.io/badge/CI-GitHub%20Actions-8b5cf6?style=flat-square" /></a>
</p>

---

### 🚀 Quick install (NO ISO)

```bash
git clone https://github.com/MoZoHuJa/OS.git ~/scarlix-os
cd ~/scarlix-os
git checkout v19.0.2   # ALWAYS checkout specific tag
bash install.sh
```

### 🧠 Inference stack (4-tier failover)

| Tier | Engine | GPU | Use case |
|------|--------|-----|----------|
| 1 | **SGLang** v0.4.6.post1-cu128 (`--disable-flashinfer`) | GPU 0 | Primary (Qwen3-14B-AWQ) |
| 2 | **vLLM** v0.8.5 (TP=1, `.experimental` only) | GPU 1 | High throughput |
| 3 | **BeeLlama** (llama.cpp, CPU) | — | Offline fallback (GGUF Q4_K_M) |
| 4 | **Ollama** (CPU) | — | Tertiary starter model |

External clients hit the **LiteLLM gateway** (`:4001`, 3-tier: SGLang → Ollama → BeeLlama). scarlix-mode's direct AI path keeps the full 4-tier.

### 🎛️ Modes (scarlix-mode)

`ai` · `turbo` · `creative` · `tv` · `game` · `offline` · `stop`

Dashboard at `:8090` (token auth, localhost only — use Tailscale/SSH tunnel for LAN).

### 📦 What's in the box

- **ScarliHQ** — Go binary dashboard + REST API + WebSocket + MCP server
- **Secure Host-Bridge** — ScarliHQ has NO docker.sock, NO nvidia runtime (privilege boundary)
- **Profiles** — Zmor (admin) · Hugo (son) · XOX (daughter) · Mon (wife)
- **Monitoring** — VictoriaMetrics + Grafana + OpenTelemetry + CrowdSec WAF
- **VPN** — Headscale (WireGuard mesh)
- **Workspace** — Buzz (Nostr relay), Gitea, Nextcloud, n8n, Coolify

---

<p align="center">
  <sub>Banner design matches the ScarliHQ dashboard (visible on the TV). Source: <a href="https://github.com/MoZoHuJa/OS/blob/main/docs/profile-banner.html">docs/profile-banner.html</a>.</sub>
</p>
