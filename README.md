### Hi, I'm Ramazan Yavuz.

This GitHub account is my personal hub for open-source projects, independent of any business work or client engagements. Anything published here is something I built, found useful, and decided to share publicly under the MIT (or similar permissive) license.

For my professional / consulting profile, see [ramazan-yavuz.tr](https://ramazan-yavuz.tr). The two are deliberately separate.

### Public projects

Categorized so things stay clear as more land here.

#### Linux tools

- **[hydra-llm](https://github.com/ra-yavuz/hydra-llm)** &nbsp; CLI + KDE Plasma 6 widget. Docker for language models, with retrieval baked in. Single-binary CLI runs each local LLM in its own llama.cpp container, with a hardware-aware curated catalog of community-quantised GGUFs that download anonymously, OpenAI-compatible endpoints on stable local ports, retrieval-augmented generation over any folder you point it at, and catalog-bound bundles that bake a model + persona + corpus into one chat alias. No telemetry, no API key.
- **[lillycoder](https://github.com/ra-yavuz/lillycoder)** &nbsp; CLI. A chat REPL that drops into any folder, where the local LLM can read, write, and edit your files, run shell commands, and install packages. Per-tool permission prompts and a hard-deny safety classifier on top of the agent loop. Talks to any OpenAI-compatible /v1 endpoint, so you bring your own server (llama.cpp, ollama, LM Studio).
- **[inhibit-charge](https://github.com/ra-yavuz/inhibit-charge)** &nbsp; CLI + daemon. Park your Linux laptop battery at a target charge level using the kernel's `inhibit-charge` mode. Unlike threshold-only tools (TLP, GNOME, KDE), the battery does not trickle-cycle on AC.
- **[herald](https://github.com/ra-yavuz/herald)** &nbsp; CLI + systemd timer. Prints a daily quote at the top of every new terminal and at login. Cached, configurable refresh, local fallback pool, optional user prefix.
- **[meowtrics](https://github.com/ra-yavuz/meowtrics)** &nbsp; A small animated emoji that lives in your system tray and gossips about your machine. KDE Plasma 6 plasmoid plus StatusNotifierItem support for GNOME / XFCE / Cinnamon / Budgie / MATE / LXQt, plus JSON output for Sway / i3 / polybar bars.

(more categories will appear here as projects in them are published.)

### Apt repository

Every Debian / Ubuntu tool above in one place, kept up to date with the rest of your system. **[ra-yavuz.github.io/apt](https://ra-yavuz.github.io/apt/)** is a single signed apt archive. Add it once, get every tool with `apt install` and `apt upgrade`, GPG-verified signatures on every package. Source: [ra-yavuz/apt](https://github.com/ra-yavuz/apt).

One line. Sets up the signed repo if not already added, refreshes the package index, and installs the package. Replace `<package>` with `inhibit-charge`, `herald`, `meowtrics`, `lillycoder`, or `hydra-llm`:

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
