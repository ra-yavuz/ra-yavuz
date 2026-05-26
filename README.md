### Hi, I'm Ramazan Yavuz.

This GitHub account is my personal hub for open-source projects, independent of any business work or client engagements. Anything published here is something I built, found useful, and decided to share publicly under the MIT (or similar permissive) license.

For my professional / consulting profile, see [ramazan-yavuz.tr](https://ramazan-yavuz.tr). The two are deliberately separate.

### Public projects

Categorized so things stay clear as more land here.

#### Linux tools

- **[portunus-ovpn](https://github.com/ra-yavuz/portunus-ovpn)** &nbsp; KDE Plasma 6 panel widget. Native panel widget for switching OpenVPN connections through NetworkManager. Import, edit, remove, export and toggle .ovpn profiles from your panel; single-active by default with optional multi-active for split-tunnel combos. Per-connection remember-passphrase toggle backed by NetworkManager secret flags and KWallet. No second VPN daemon, no third-party PPA: drives the standard nmcli + NetworkManager + KWallet stack that already ships on KDE. Named after Portunus, the Roman god of keys and gates.
- **[hydra-llm](https://github.com/ra-yavuz/hydra-llm)** &nbsp; CLI + KDE Plasma 6 widget. Docker for language models, with retrieval baked in. Single-binary CLI runs each local LLM in its own llama.cpp container, with a hardware-aware curated catalog of community-quantised GGUFs that download anonymously, OpenAI-compatible endpoints on stable local ports, retrieval-augmented generation over any folder you point it at, and catalog-bound bundles that bake a model + persona + corpus into one chat alias. No telemetry, no API key.
- **[lillycoder](https://github.com/ra-yavuz/lillycoder)** &nbsp; CLI. A chat REPL that drops into any folder, where the local LLM can read, write, and edit your files, run shell commands, and install packages. Per-tool permission prompts and a hard-deny safety classifier on top of the agent loop. Talks to any OpenAI-compatible /v1 endpoint, so you bring your own server (llama.cpp, ollama, LM Studio).
- **[hydra-rag-hooks](https://github.com/ra-yavuz/hydra-rag-hooks)** &nbsp; UserPromptSubmit hooks for both Anthropic's Claude Code AND OpenAI's Codex CLI from one `apt install`. Type `rag <question>` in either CLI; the first `rag` in a project folder fork-detaches a background indexer, the next `rag` retrieves the top relevant chunks from a per-folder LanceDB index and prepends them to the prompt before the model sees it. Both CLIs share the same `.hydra-index/` store, the same toggles, and the same bundled MCP server for model-decided retrieval. apt install wires Claude Code via `/etc/claude-code/managed-settings.json`; one `codex plugin add` per user enables Codex. Successor to `claude-rag-hook` v0.6.x; existing `.claude-rag-index/` folders are auto-renamed in place on first run. Pairs with `hydra-llm` for shared embedder and store.
- **[inhibit-charge](https://github.com/ra-yavuz/inhibit-charge)** &nbsp; CLI + daemon. Park your Linux laptop battery at a target charge level using the kernel's `inhibit-charge` mode. Unlike threshold-only tools (TLP, GNOME, KDE), the battery does not trickle-cycle on AC.
- **[herald](https://github.com/ra-yavuz/herald)** &nbsp; CLI + systemd timer. Prints a daily quote at the top of every new terminal and at login. Cached, configurable refresh, local fallback pool, optional user prefix.
- **[meowtrics](https://github.com/ra-yavuz/meowtrics)** &nbsp; A small animated emoji that lives in your system tray and gossips about your machine. KDE Plasma 6 plasmoid plus StatusNotifierItem support for GNOME / XFCE / Cinnamon / Budgie / MATE / LXQt, plus JSON output for Sway / i3 / polybar bars.

#### Docs & guides

- **[vigil](https://github.com/ra-yavuz/vigil)** &nbsp; How to build an always-on, autonomous AI operations assistant, and how to keep it diligent. A documentation project describing the architecture of a persistent AI operator (persistent agent subprocess, supervisor, transport split, channel multiplexers, MCP tools) as a reference design, plus the load-bearing piece most write-ups skip: the doctrine + hooks pattern that re-asserts an engineering standard on every turn so an auto-approved agent keeps verifying before it acts, refuses workarounds, and never claims done without a real run. Ships a generic `doctrine.md`, both Claude Code hook scripts, and a `settings.json` fragment.

(more categories will appear here as projects in them are published.)

### Apt repository

Every Debian / Ubuntu tool above in one place, kept up to date with the rest of your system. **[ra-yavuz.github.io/apt](https://ra-yavuz.github.io/apt/)** is a single signed apt archive. Add it once, get every tool with `apt install` and `apt upgrade`, GPG-verified signatures on every package. Source: [ra-yavuz/apt](https://github.com/ra-yavuz/apt).

One line. Sets up the signed repo if not already added, refreshes the package index, and installs the package. Replace `<package>` with `inhibit-charge`, `herald`, `meowtrics`, `lillycoder`, `hydra-llm`, `hydra-rag-hooks`, or `portunus-ovpn`:

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
