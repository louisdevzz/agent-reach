# Agent Reach — Installation Guide

## For Humans

Copy this to your AI Agent:

```
Install Agent Reach: https://raw.githubusercontent.com/louisdevzz/agent-reach/main/docs/install.md
```

> 🛡️ **Security-conscious?** Use safe mode — it won't auto-install system packages:
> ```
> Install Agent Reach (safe mode): https://raw.githubusercontent.com/louisdevzz/agent-reach/main/docs/install.md
> Use the --safe flag during install
> ```

---

## For AI Agents

### Goal

Install Agent Reach and all upstream tools so your user's agent has full internet access. After installation, you'll use the upstream tools directly (OpenCLI, twitter-cli, bili-cli, rdt-cli, yt-dlp, mcporter, gh CLI, etc.) — Agent Reach is the selector, installer, health checker and router, never a wrapper.

### ⚠️ Boundaries

When fixing issues, stay within these limits:

- **DO NOT** run commands with `sudo` unless the user explicitly approved
- **DO NOT** modify system files outside `~/.agent-reach/`
- **DO NOT** install packages not listed in this guide
- **DO NOT** disable firewalls, security settings, or system protections
- **DO NOT** clone repos, create files, or run commands inside the agent workspace / working directory
- If something requires elevated permissions, **tell the user** what's needed and let them decide

### 📁 Directory Rules

All Agent Reach files go in dedicated directories — **never in the agent workspace**:

| Purpose | Directory | Example |
|---------|-----------|---------|
| Config & tokens | `~/.agent-reach/` | `~/.agent-reach/config.json` |
| Upstream tool repos | `~/.agent-reach/tools/` | `~/.agent-reach/tools/xiaoyuzhou/` |
| Temporary files | `/tmp/` | `/tmp/yt-dlp-output/` |
| Skills | `~/.agents/skills/agent-reach/` | SKILL.md |

**Why?** If you clone repos or create files in the workspace, it pollutes the user's project directory and can break their agent over time. Keep the workspace clean.

### Step 1: Install the basics

```bash
# Recommended: pipx (hassle-free)
pipx install https://github.com/louisdevzz/agent-reach/archive/main.zip
agent-reach install --env=auto

# If your Python is from Homebrew / you hit PEP 668 (externally-managed-environment)
# Use a virtual environment:
python3 -m venv ~/.agent-reach-venv
source ~/.agent-reach-venv/bin/activate
pip install https://github.com/louisdevzz/agent-reach/archive/main.zip
agent-reach install --env=auto
```

> 💡 **Windows / Microsoft Store Python alias?**
> If `python3 --version` opens the Microsoft Store, or `where python3` points to
> `...\AppData\Local\Microsoft\WindowsApps\python3.exe`, then `python3` is a Windows
> Store alias, not a usable Python installation. Use the Python Launcher `py -3` instead,
> or `python.exe` from the actual installation directory.
>
> PowerShell example:
> ```powershell
> py -3 -m venv $env:USERPROFILE\.agent-reach-venv
> $env:USERPROFILE\.agent-reach-venv\Scripts\Activate.ps1
> python -m pip install https://github.com/louisdevzz/agent-reach/archive/main.zip
> agent-reach install --env=auto
> ```

This installs core infrastructure (gh CLI, Node.js, mcporter, Exa search, yt-dlp config) and activates these zero-config channels:

- Web (Jina Reader), YouTube, GitHub, RSS, Exa Search, V2EX, Bilibili (basic)

> 💡 **macOS / Homebrew Python says `externally-managed-environment`?**
> This is PEP 668 protection, not an Agent Reach issue. Prefer `pipx install ...`, or create a `venv` first.

**Safe mode / Dry run:**

```bash
agent-reach install --env=auto --safe      # Check only, no auto-install
agent-reach install --env=auto --dry-run   # Preview what would be done
```

### Step 2: Ask the user which optional channels they want

After installing the basics, **ask the user** which additional channels they need. Present this list:

> The basics are installed! You can now search the web, browse YouTube, read GitHub repos, and more.
>
> Here are optional channels you can unlock — which ones do you need?
>
> - 🌟 **OpenCLI** (recommended for desktop) — one install unlocks XiaoHongShu, Reddit, Bilibili subtitles, and Twitter fallback (reuses your browser login session, zero config; just one Chrome Web Store click to add the extension)
> - 🐦 **Twitter/X** — search tweets, browse timeline (requires login cookie)
> - 📈 **Xueqiu** — stock quotes, hot posts (requires login cookie)
> - 🎙️ **Xiaoyuzhou Podcast** — audio to text transcription (needs free Groq API key)
> - 📕 **XiaoHongShu** — search, read, comment (desktop: OpenCLI; server: xiaohongshu-mcp QR login)
> - 📖 **Reddit** — search and read posts (login required: desktop OpenCLI or rdt-cli + cookie)
> - 📺 **Bilibili (full)** — trending, rankings, search, video details (bili-cli, no login needed)
> - 💼 **LinkedIn** — profiles, job search
>
> Tell me which ones you want, e.g. "install XiaoHongShu and Twitter" or "install all of them."

Based on the user's choice, run:

```bash
agent-reach install --env=auto --channels=opencli,xiaohongshu   # Example: desktop user chose XHS (OpenCLI-backed)
agent-reach install --env=auto --channels=all              # User wants everything
```

Supported channel names: `opencli`, `twitter`, `xiaoyuzhou`, `xueqiu`, `xiaohongshu`, `reddit`, `bilibili`, `linkedin`, `all`

### Step 3: Fix what's broken

Run `agent-reach doctor` and check the output.

Try to get as many channels to ✅ as possible. If something failed during install or shows as ❌/⚠️ in doctor, diagnose the problem and try to fix it — but stay within the boundaries above. If a fix requires elevated permissions or system changes, ask the user first.

Only ask the user when you genuinely need their input (credentials, permissions, etc.).

### Step 3: Configure things that need user input

Some channels need credentials only the user can provide. Based on the doctor output, ask for what's missing:

> 🔒 **Security tip:** For platforms that need cookies (Twitter, XiaoHongShu), we recommend using a **dedicated/secondary account** rather than your main account. Cookie-based auth carries two risks:
> 1. **Account ban** — platforms may detect non-browser API calls and restrict or ban the account
> 2. **Credential exposure** — cookies grant full account access; using a secondary account limits the blast radius if credentials are ever compromised

> 🍪 **Cookie import (works for all platforms that need login):**
>
> For all platforms requiring cookies (Twitter, XiaoHongShu, Xueqiu, etc.), **prefer Cookie-Editor import** — the simplest and most reliable method:
> 1. User logs into the target platform in their browser
> 2. Install the [Cookie-Editor](https://chromewebstore.google.com/detail/cookie-editor/hlkenndednhfkekhgcdicdfddnkalmdm) Chrome extension
> 3. Click the extension → Export → Header String
> 4. Send the exported string to the Agent
>
> **Local desktop users** can also use `agent-reach configure --from-browser chrome` to auto-extract in one command (supports Twitter + XiaoHongShu + Xueqiu).

**Twitter search & posting:**
> "To unlock Twitter search, I need your Twitter cookies. Install the Cookie-Editor Chrome extension, go to x.com/twitter.com, click the extension → Export → Header String, and paste it to me."

```bash
agent-reach configure twitter-cookies "PASTED_STRING"
```

> **Proxy setup (for networks behind firewalls, e.g. mainland China):**
>
> twitter-cli and rdt-cli use Python and can be configured with environment variables for proxied networks.
>
> **You (Agent) need to:**
> 1. Confirm user has a proxy: `agent-reach configure proxy http://user:pass@ip:port`
> 2. Set environment variables: `export HTTP_PROXY="..." HTTPS_PROXY="..."`
> 3. Agent Reach handles the rest automatically
>
> If the user reports "fetch failed", see [troubleshooting.md](troubleshooting.md)

**Reddit (login is mandatory — no zero-config path):**
> Reddit's anonymous endpoints are blocked and the official API requires manual approval. Desktop users should use OpenCLI (just log into reddit.com in your browser). For server/legacy users, use rdt-cli:

```bash
# PyPI lags behind — install from GitHub (pinned to the same commit as _RDT_GIT_SOURCE in the code)
pipx install 'git+https://github.com/public-clis/rdt-cli.git@5e4fb3720d5c174e976cd425ccc3b879d52cac66'
rdt login   # Auto-extract browser cookies; on servers without browsers, follow doctor prompts for manual cookie setup
```

> Mainland China users need a proxy to access Reddit; server IPs may be rate-limited — consider a residential proxy (e.g. https://webshare.io, ~$1/month):
> ```bash
> agent-reach configure proxy http://user:pass@ip:port
> ```

**XiaoHongShu / 小红书 (multi-backend, environment-aware):**

> **Desktop (recommended: OpenCLI):**
> "XiaoHongShu uses OpenCLI — it reuses your browser login session. If you've browsed XiaoHongShu before, it just works, zero config."

```bash
agent-reach install --channels opencli
```

> After installation, guide the user through the one manual step (Chrome security restriction, can't automate):
> 1. Open https://chromewebstore.google.com/detail/opencli/ildkmabpimmkaediidaifkhjpohdnifk
> 2. Click "Add to Chrome"
> 3. Run `opencli doctor` to verify (should show "Extension: connected")
>
> **Server / no desktop environment (xiaohongshu-mcp):**
> 1. Download the platform binary from https://github.com/xpzouying/xiaohongshu-mcp/releases to `~/.agent-reach/tools/`
> 2. Start the service (first run auto-downloads ~150MB headless browser)
> 3. Have user scan QR to log in (agent calls `get_login_qrcode` tool for QR code)
> 4. Connect: `mcporter config add xiaohongshu http://localhost:18060/mcp`
> 5. Always use `--timeout 120000` when calling
>
> **Existing users (xhs-cli):** Already-installed xhs-cli continues to work as a fallback backend (upstream unmaintained since 2026-03, not recommended for new installs). `xhs login` auto-extracts browser cookies; if it fails, use Cookie-Editor to export, then:
> ```bash
> agent-reach configure xhs-cookies "key1=val1; key2=val2; ..."
> ```

**Xueqiu (stock quotes + hot posts):**
> "Xueqiu needs your login cookie. Log into xueqiu.com in Chrome first, then run:"

```bash
agent-reach configure --from-browser chrome
```

> Cookies are extracted automatically along with other platforms.

**Xiaoyuzhou Podcast (Groq Whisper):**
> "Xiaoyuzhou podcast transcription is installed by default — you just need a free Groq API key."

The script is auto-installed with Agent Reach. Just provide the key:

```bash
agent-reach configure groq-key gsk_xxxxx
```

> **Getting a Groq API key (free, no credit card, 30 seconds):**
> 1. Open https://console.groq.com
> 2. Sign in with Google/GitHub (or register)
> 3. Left menu → API Keys → Create API Key
> 4. Copy the key (starts with `gsk_`), send it to your Agent
>
> **Usage:**
> Send a Xiaoyuzhou link to your Agent, it auto-runs:
> ```bash
> bash ~/.agent-reach/tools/xiaoyuzhou/transcribe.sh https://www.xiaoyuzhoufm.com/episode/xxxxx
> ```
>
> Auto-download audio → transcode and chunk → Groq Whisper transcription → output full transcript.
>
> **Free limits:**
> - ~2 hours of audio per hour (7200 seconds); retry after 15 minutes if exceeded
> - Plenty for daily podcast listening
> - High-quality transcription (Whisper large-v3), but no speaker diarization
> - For episodes over 2 hours, consider processing in batches

**LinkedIn (optional — linkedin-scraper-mcp):**
> "LinkedIn basic content can be read via Jina Reader. Full features (profile details, job search) need linkedin-scraper-mcp."

```bash
pip install linkedin-scraper-mcp
```

> **Login (requires a browser UI):**
>
> linkedin-scraper-mcp uses Chromium and needs a visible browser window.
>
> - **Local desktop (has a display):** Just run:
>   ```bash
>   linkedin-scraper-mcp --login --no-headless
>   ```
>   A browser window will open — log into LinkedIn manually.
>
> - **Server (no UI):** Use VNC for remote desktop:
>   ```bash
>   # 1. Install and start VNC on server (skip if already set up)
>   apt install -y tigervnc-standalone-server
>   vncserver :1 -geometry 1280x720
>   
>   # 2. Connect with a VNC client to server-ip:5901
>   
>   # 3. In the VNC desktop terminal, run:
>   export DISPLAY=:1
>   linkedin-scraper-mcp --login --no-headless
>   ```
>   Log in when the browser appears. The session is saved to `~/.linkedin-mcp/profile/`.
>
> **After login, start the MCP service:**
> ```bash
> linkedin-scraper-mcp --transport streamable-http --port 8001
> mcporter config add linkedin http://localhost:8001/mcp
> ```
>
> See https://github.com/stickerdaniel/linkedin-mcp-server for more details.

### Step 4: Final check

Run `agent-reach doctor` one final time and report the results to your user.

### Step 5: Set up daily monitoring (OpenClaw only)

If you are running inside **OpenClaw**, ask your user:

> "Agent Reach is installed. Want me to set up a daily health check? It monitors whether all channels are working and checks for new versions. It only notifies you when there's a problem."

If the user agrees, create a **cron job** (daily, `sessionTarget: "isolated"`, `delivery: "announce"`) with this task:

```
Run agent-reach watch.
If the output says "everything is fine," end silently — don't notify the user.
If there are issues (❌ ⚠️) or a new version (🆕), send the full report to the user with suggested fixes.
If a new version is available, ask the user if they want to upgrade (send this to the user's Agent: Update Agent Reach: https://raw.githubusercontent.com/louisdevzz/agent-reach/main/docs/update.md).
```

If the user wants a different agent to handle it, let them choose.

---

## Quick Reference

| Command | What it does |
|---------|-------------|
| `agent-reach install --env=auto` | Install core channels (lightweight, zero-config) |
| `agent-reach install --env=auto --channels=twitter,xiaohongshu` | Install core + optional channels |
| `agent-reach install --env=auto --channels=all` | Install everything |
| `agent-reach install --env=auto --safe` | Safe setup (no auto system changes) |
| `agent-reach install --env=auto --dry-run` | Preview what would be done |
| `agent-reach doctor` | Show channel status |
| `agent-reach watch` | Quick health + update check (for scheduled tasks) |
| `agent-reach check-update` | Check for new versions |
| `agent-reach configure twitter-cookies "..."` | Unlock Twitter search + posting |
| `agent-reach configure proxy URL` | Save proxy address (Agent reads it when accessing restricted networks like Reddit/Twitter to set HTTP_PROXY/HTTPS_PROXY — not an auto-unlock switch) |
| `agent-reach configure groq-key gsk_xxx` | Unlock Xiaoyuzhou podcast transcription |

After installation, use upstream tools directly. See SKILL.md for the full command reference:

| Platform | Upstream Tool | Example |
|----------|--------------|---------|
| Twitter/X | `twitter` (fallback `opencli`) | `twitter search "query" -n 10` |
| YouTube | `yt-dlp` | `yt-dlp --dump-json URL` |
| Bilibili | `bili` (subtitles via `opencli`) | `bili search "query" --type video` / `opencli bilibili subtitle BVxxx` |
| Reddit | `opencli` (fallback `rdt`) | `opencli reddit search "query" -f yaml` / `rdt read POST_ID` |
| GitHub | `gh` | `gh search repos "query"` |
| Web | `curl` + Jina | `curl -s "https://r.jina.ai/URL"` |
| Exa Search | `mcporter` | `mcporter call 'exa.web_search_exa(...)'` |
| XiaoHongShu | `opencli` (server `mcporter`) | `opencli xiaohongshu search "query" -f yaml` |
| Xiaoyuzhou Podcast | `transcribe.sh` | `bash ~/.agent-reach/tools/xiaoyuzhou/transcribe.sh <URL>` |
| LinkedIn | `mcporter` | `mcporter call 'linkedin.get_person_profile(...)'` |
| RSS | `feedparser` | `python3 -c "import feedparser; ..."` |

> For multi-backend platforms, check `agent-reach doctor --json` for `active_backend`.
