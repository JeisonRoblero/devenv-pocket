# devenv-pocket

<!-- markdownlint-disable MD033 -->
<div align="center">
  <img width="auto" height="400" alt="devenv-pocket Banner" src="https://github.com/user-attachments/assets/b691eb28-c1e4-4eb7-a8eb-3763fa4f64b2" />
  &nbsp;
</div>
<!-- markdownlint-enable MD033 -->

Your full developer workstation, in your pocket.  
Turn your Android phone into an automated, high-performance developer sandbox - any distribution, headless or desktop graphical display, fully configured offline, no root required.  
Run React/Vite web services, Flutter/Android compilations, and PostgreSQL database servers on ARM64 systems.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Platform: Termux](https://img.shields.io/badge/Platform-Termux-green.svg)](https://termux.dev/)
[![Language: Bash](https://img.shields.io/badge/Language-Bash-4EAA25.svg)](https://www.gnu.org/software/bash/)

<!-- markdownlint-disable MD033 -->
<br>

<div align="center">
<a href="https://cdn.jsdelivr.net/gh/JeisonRoblero/devenv-pocket@main/devenv-pocket" target="_blank" rel="noopener noreferrer">
  <img src="https://img.shields.io/badge/DOWNLOAD_SCRIPT-Direct_Download_Link-0078D4?style=for-the-badge&logo=git&logoColor=white" alt="Download devenv-pocket" />
</a>
</div>
<!-- markdownlint-enable MD033 -->

---

## Core Features

- **Dual Execution Environments**: Toggle between **Graphical Desktop** (for running Chrome/X11 debugging) and **Terminal / Headless Mode** (bypasses heavy GUI layers to save ~1.2 GB size, exposing lightweight coding interfaces).
- **Automated ARM64 Native Patches**: Automatically replaces standard x86-64 SDK binaries with high-performance community ARM64 compiled ports (links `adb`, `aapt`, `aapt2`, `cmake`, and `ninja`, NDK r28c toolchains, and patches gradle jar caches).
- **Instant Project Templates (Offline in 3s)**: Pre-caches standard templates in centralized content-addressable storage (`~/.local/share/pnpm/store` for Node, `~/.pub-cache` and `~/.gradle/caches` for Flutter). Instantiate projects offline using a simple CLI copy utility!
- **User-Friendly Wizard**: An interactive dashboard showing status cards, estimated disk sizes, diagnostics, and a progress spinner. Handles complex PPA priorities, licensing, and databases silently.
- **Embedded Web Code Editors**: Seamlessly configures VS Code inside your phone's browser (`code-server` with `cs` command) and python-based local FTP servers to connect Acode.

<!-- markdownlint-disable MD033 -->
<p align="center">
  <img src="https://github.com/user-attachments/assets/5599e3c8-b2b4-4ccc-b650-52e3270a018c" width="98%" alt="devenv-pocket Execution Modes" />
</p>
<!-- markdownlint-enable MD033 -->

---

## Requirements

This tool runs **inside** a Linux container (such as Ubuntu inside `proot-distro` on Termux) on ARM64 Android processors.

- **Primary Shell**: [Termux on F-Droid](https://f-droid.org/packages/com.termux/) (Do not use Google Play Store version).
- **Distro Manager**: Installed Termux distro via `pkg install proot-distro && proot-distro install ubuntu`.
- **Graphical Displays** (Optional): For running web debugging, install [Termux:X11 (GitHub)](https://github.com/termux/termux-x11/releases) and recommend using [groot-desk](https://github.com/JeisonRoblero/groot-desk) outside in Termux to manage the displays.

---

## Installation

To download and register the script globally as a system command, log into your distribution as root and run the following:

```bash
curl -sL "https://raw.githubusercontent.com/JeisonRoblero/devenv-pocket/main/devenv-pocket" -o devenv-pocket && chmod +x devenv-pocket && ./devenv-pocket
```

The script automatically registers itself under `/usr/local/bin/devenv-pocket` on the first execution. Once registered, invoke the wizard from any directory:

```bash
devenv-pocket
```

---

## Interactive Setup Wizard Flow

By running `devenv-pocket`, an interactive dashboard launch checks system packages and displays available options:

1. **System & Status Scan**
   Checks the distro for packages (`nodejs`, `openjdk-17`, `clang`, `postgresql`, `pnpm`, `flutter`, `NDK`) and displays their current states (`[Installed]`, `[Partially Installed]`, or `[Not Installed]`).

2. **Graphical vs Terminal Setup**
   Guides you to choose the execution path, warning you about download sizes (~150 MB for terminal Node vs ~1.2 GB for graphical layout containing Chromium).

3. **Obvious Settings Automation**
   Handles Android licenses, dockerenv root warning bypasses, custom NDK r28c toolchain edits, and PostgreSQL data directory permissions (`chown postgres`) silently.

4. **Dedicated Code Editors Setup**
   Prompts you to select code editors: code-server (starts VS Code in Android browser), pyftpdlib (FTP on port 2121 for Acode), direct storage maps, or both.

5. **Clean Uninstallation Dashboard**
   Option `[5]` allows to cleanly purge directory structures and wipe corresponding `.bashrc` modifications, returning the system to a clean state.

---

## Command Reference

`devenv-pocket` supports direct CLI command arguments and flags to bypass interactive menus:

### CLI Commands

| Command | Action |
| --- | --- |
| `devenv-pocket` | Setup wizard - launch interactive dashboard dashboard |
| `devenv-pocket install <env>` | Unattended setup of a profile (`node`, `flutter`, `postgres`, `all`) |
| `devenv-pocket remove <env>` | Safe automated removal of a profile & configuration cleanups |
| `devenv-pocket status` | Display detailed system diagnostics & component states |
| `devenv-pocket patch` | Patch local x86_64 `aapt2` binaries inside existing Gradle jar cache directories |
| `devenv-pocket ftpstart` | Start Python background FTP sharing on port 2121 for Acode |
| `devenv-pocket ftpstop` | Stop Python background FTP server |
| `devenv-pocket create <temp> <name>` | Instantiate a new project instantly offline from cached templates |
| `devenv-pocket offline [on \| off]` | Enable or disable Gradle compile offline mode parameters |
| `devenv-pocket help` | Show command-line visual helper menu |

### CLI Modifiers / Flags

* `--terminal` or `-t` : Enforce Terminal / Headless mode configurations.
* `--graphical` or `-g` : Enforce Graphical Desktop mode (X11 Chromium / PPA).
* `--editor=<opt>` or `-e=<opt>` : Override editor setups (`codeserver`, `ftp`, `both`, `none`).
* `--offline` or `-o` : Automatically populates/caches offline environment starter libraries.

---

## Offline Project Templates Mappings

Using `devenv-pocket create <temp> <project-name>` duplicates cached structures instantly in under 3 seconds:

- **`react`** (`react-vite-ts`): Standard React application set up with Vite, TypeScript, and pnpm Content-Addressable Storage (shares packages globally, saving massive phone space).
- **`node`** (`node-postgres`): Backend setup with Express, PostgreSQL driver, and Drizzle-ORM.
- **`flutter`** (`flutter-starter`): Flutter template configured with API 34 overrides (so it builds out-of-the-box on ARM64) and pre-compiled to cache Gradle/Maven wrapper dependencies (~700 MB cached).

---

## PostgreSQL Service Control

PostgreSQL runs natively inside proot Ubuntu using custom aliases added automatically to your `~/.bashrc`:

* **`pgstart`** : Starts the PostgreSQL server safely.
* **`pgstop`**  : Stops the database server gracefully.
* **`pgdb`**    : Opens the PostgreSQL interactive command client shell (`psql`).

---

## Contributing

Contributions are welcome! Whether you are reporting bugs, requesting features, or submitting a Pull Request, check out the [Contributing Guidelines](CONTRIBUTING.md) to get started.

---

## Support

If this project has been useful to you, consider buying me a coffee - it genuinely helps keep the work going.

<!-- markdownlint-disable MD033 -->
<div align="center">

[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20on%20Ko--fi-FF5E5B?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/JeisonRoblero)
[![PayPal](https://img.shields.io/badge/PayPal-Donate%20via%20PayPal-003087?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/JeisonRoblero)

</div>
<!-- markdownlint-enable MD033 -->
