### Hi, I'm Ramazan Yavuz.

This GitHub account is my personal hub for open-source projects, independent of any business work or client engagements. Anything published here is something I built, found useful, and decided to share publicly under the MIT (or similar permissive) license.

For my professional / consulting profile, see [ramazan-yavuz.tr](https://ramazan-yavuz.tr). The two are deliberately separate.

### Public projects

Categorized so things stay clear as more land here.

#### Linux tools

- **[claude-can-speak](https://github.com/ra-yavuz/claude-can-speak)** &nbsp; npm CLI + Claude Code skill & hook. Lets Claude Code decide what to say out loud. Most "speak Claude aloud" tools read every reply at you; this one leads with a `speak` skill that lets Claude voice only what is worth hearing (a spoken "build is done", a heads-up while you look away, a shoutout), while everything else stays text. A speak-everything firehose with its own on/off switch (off by default) is included too, but the deliberate skill is the point. Local neural text-to-speech runs in Docker, Kokoro for natural English and Piper for German, Turkish, and more, so nothing goes to the cloud and there are no API keys. `npm install -g claude-can-speak`.
- **[edgecall](https://github.com/ra-yavuz/edgecall)** &nbsp; CLI + API. Route a plain-language request to one of your own functions, using a deliberately weak local model. A small self-hosted, OpenAI-compatible API: you POST a sentence and a tiny model (phi3-class, the kind that runs on a Raspberry Pi or a phone) reads a short paginated menu of your registered functions, picks one, and edgecall runs it and returns the result. The model never sees the whole list at once; it pages through a few options at a time with a "next" choice, so all a weak model has to do is pick one item off a short menu. No embedding model, no index to maintain. Add a function by dropping in a Python file with an id and a one-line description. Talks to any OpenAI-compatible `/v1` endpoint (llama.cpp, ollama, LM Studio, hydra-llm).
- **[portunus-ovpn](https://github.com/ra-yavuz/portunus-ovpn)** &nbsp; KDE Plasma 6 panel widget. Native panel widget for switching OpenVPN connections through NetworkManager. Import, edit, remove, export and toggle .ovpn profiles from your panel; single-active by default with optional multi-active for split-tunnel combos. Per-connection remember-passphrase toggle backed by NetworkManager secret flags and KWallet. No second VPN daemon, no third-party PPA: drives the standard nmcli + NetworkManager + KWallet stack that already ships on KDE. Named after Portunus, the Roman god of keys and gates.
- **[hydra-llm](https://github.com/ra-yavuz/hydra-llm)** &nbsp; CLI + KDE Plasma 6 widget. Docker for language models, with retrieval baked in. Single-binary CLI runs each local LLM in its own llama.cpp container, with a hardware-aware curated catalog of community-quantised GGUFs that download anonymously, OpenAI-compatible endpoints on stable local ports, retrieval-augmented generation over any folder you point it at, and catalog-bound bundles that bake a model + persona + corpus into one chat alias. No telemetry, no API key.
- **[lillycoder](https://github.com/ra-yavuz/lillycoder)** &nbsp; CLI. A chat REPL that drops into any folder, where the local LLM can read, write, and edit your files, run shell commands, and install packages. Per-tool permission prompts and a hard-deny safety classifier on top of the agent loop. Talks to any OpenAI-compatible /v1 endpoint, so you bring your own server (llama.cpp, ollama, LM Studio).
- **[hydracoder](https://github.com/ra-yavuz/hydracoder)** &nbsp; Web UI + orchestrator. Enter a project goal and local models plan it, build it, and review it, with no hosted AI in the loop. A planner turns the goal into a task graph, a scheduler routes each task to a right-sized local model, a reviewer checks each result, and an append-only journal makes a crash or a full context window recoverable. A dark UI shows each model as a live terminal and a chat box steers the run in plain language. Built on `hydra-llm` (model substrate) and `lillycoder` (agent loop), so it runs entirely on your own hardware. Made to keep development moving when hosted AI becomes too expensive to use.
- **[hydra-rag-hooks](https://github.com/ra-yavuz/hydra-rag-hooks)** &nbsp; UserPromptSubmit hooks for both Anthropic's Claude Code AND OpenAI's Codex CLI from one `apt install`. Type `rag <question>` in either CLI; the first `rag` in a project folder fork-detaches a background indexer, the next `rag` retrieves the top relevant chunks from a per-folder LanceDB index and prepends them to the prompt before the model sees it. Both CLIs share the same `.hydra-index/` store, the same toggles, and the same bundled MCP server for model-decided retrieval. apt install wires Claude Code via `/etc/claude-code/managed-settings.json`; one `codex plugin add` per user enables Codex. Successor to `claude-rag-hook` v0.6.x; existing `.claude-rag-index/` folders are auto-renamed in place on first run. Pairs with `hydra-llm` for shared embedder and store.
- **[inhibit-charge](https://github.com/ra-yavuz/inhibit-charge)** &nbsp; CLI + daemon. Park your Linux laptop battery at a target charge level using the kernel's `inhibit-charge` mode. Unlike threshold-only tools (TLP, GNOME, KDE), the battery does not trickle-cycle on AC.
- **[herald](https://github.com/ra-yavuz/herald)** &nbsp; CLI + systemd timer. Prints a daily quote at the top of every new terminal and at login. Cached, configurable refresh, local fallback pool, optional user prefix.
- **[meowtrics](https://github.com/ra-yavuz/meowtrics)** &nbsp; A small animated emoji that lives in your system tray and gossips about your machine. KDE Plasma 6 plasmoid plus StatusNotifierItem support for GNOME / XFCE / Cinnamon / Budgie / MATE / LXQt, plus JSON output for Sway / i3 / polybar bars.
- **[doublethink](https://github.com/ra-yavuz/doublethink)** &nbsp; CLI + broker + Android app. ntfy you can actually trust: a publish/subscribe message broker as easy to stand up as ntfy, but with genuinely private channels. ntfy is effortless because its topic name is the only gate, which is also why its topics are effectively public. doublethink keeps the minutes-to-set-up ergonomics and adds real privacy: creating a private channel is self-service (one request, no operator) and returns a high-entropy shared secret. That secret is the gate, whoever holds it can join the channel and no one else can, and the broker never sees it (it stores only a derived authentication key), so messages are end-to-end encrypted between the parties who share the secret and the operator cannot read them. Knowing a channel name grants no access. Bidirectional, asynchronous, streaming, with opt-in plaintext public topics too. Cross-platform: run it in Docker or as a single native binary (Go). A sideloadable Android app subscribes to topics and raises a notification when a message arrives.
- **[agent-doublethink](https://github.com/ra-yavuz/agent-doublethink)** &nbsp; MCP server (single static binary). Keep two coding agents on two machines working the same project in sync, over a channel the broker cannot read. Point Claude Code, Codex, or Gemini at it, and a partner agent on another machine at the same channel, and the two exchange plans, decisions, blockers, and divergence flags as they work. Traffic is end-to-end encrypted over doublethink, so the broker only ever sees ciphertext. Roles are discovered automatically (the agent that creates the channel is A, the one that joins is B). A one-line digest of your partner's state is surfaced at the start of each turn, only when something changed, so drift surfaces early instead of at merge time. Hand the install prompt's URL to your agent and it sets itself up: downloads the binary, registers the MCP server, and connects. Works the same on all three agents (each gets a one-command MCP registration and a per-turn hook).

#### Docs & guides

- **[vigil](https://github.com/ra-yavuz/vigil)** &nbsp; How to build an always-on, autonomous AI operations assistant, and how to keep it diligent. A documentation project describing the architecture of a persistent AI operator (persistent agent subprocess, supervisor, transport split, channel multiplexers, MCP tools) as a reference design, plus the load-bearing piece most write-ups skip: the doctrine + hooks pattern that re-asserts an engineering standard on every turn so an auto-approved agent keeps verifying before it acts, refuses workarounds, and never claims done without a real run. Ships a generic `doctrine.md`, both Claude Code hook scripts, and a `settings.json` fragment.

(more categories will appear here as projects in them are published.)

### Apt repository

Every Debian / Ubuntu tool above in one place, kept up to date with the rest of your system. **[ra-yavuz.github.io/apt](https://ra-yavuz.github.io/apt/)** is a single signed apt archive. Add it once, get every tool with `apt install` and `apt upgrade`, GPG-verified signatures on every package. Source: [ra-yavuz/apt](https://github.com/ra-yavuz/apt).

One line. Sets up the signed repo if not already added, refreshes the package index, and installs the package. Replace `<package>` with `inhibit-charge`, `herald`, `meowtrics`, `lillycoder`, `hydra-llm`, `hydracoder`, `hydra-rag-hooks`, `portunus-ovpn`, or `edgecall`:

```bash
sudo bash -c 'set -e; install -m 0755 -d /etc/apt/keyrings && curl -fsSL https://ra-yavuz.github.io/apt/pubkey.gpg -o /etc/apt/keyrings/ra-yavuz.gpg && echo "deb [signed-by=/etc/apt/keyrings/ra-yavuz.gpg] https://ra-yavuz.github.io/apt stable main" > /etc/apt/sources.list.d/ra-yavuz.list && apt update && apt install -y <package>'
```

Once the repo is set up, future installs and upgrades are just `sudo apt update && sudo apt install <package>` and `sudo apt upgrade`. The `sudo apt update` step is required, without it apt will not see new packages or new versions.

**Tested on Ubuntu (Linux only).** Should work on any recent Debian / Ubuntu derivative, and on **WSL2** Ubuntu for the projects that don't depend on hardware sysfs or a Linux desktop tray. **macOS** support is per-project: `hydra-llm` runs under Docker Desktop and `lillycoder` installs from source via `pip`; the rest are Linux-only by design. Each project page has its own *Platform support* section.

If you don't want to add a third-party apt source, every release also attaches a prebuilt `.deb` to its GitHub Releases page.

### Hub

[ra-yavuz.github.io](https://ra-yavuz.github.io/) collects all of the above with filterable categories.

### About

Independent engineer based between Arnsberg, Germany and Antalya, Turkey. Working languages: English, German, Turkish.

### Disclaimer

All software published from this account is provided **as is, without warranty of any kind**. Some projects interact with low-level system interfaces and may affect your hardware. I am not liable for any damage to hardware, data, or system caused by installing or running these projects. Read each project's README and project page before installing.

### Contact

For consulting or business: see [ramazan-yavuz.tr](https://ramazan-yavuz.tr).
