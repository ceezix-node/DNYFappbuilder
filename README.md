
<div align="center">

```
 █████╗ ██████╗ ██████╗
██╔══██╗██╔══██╗██╔══██╗
███████║██████╔╝██████╔╝
██╔══██║██╔══██╗██╔═══╝
██║  ██║██████╔╝██║
╚═╝  ╚═╝╚═════╝ ╚═╝
```

### `DNYFappbuilder v2.2.0`
**Autonomous Multi-Language Build Intelligence**

*Detect → Build → Sign → Install → Deploy — one CLI, every platform, zero friction*

---

[![Build & Test](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/build.yml/badge.svg)](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/build.yml)
[![Release](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/release.yml/badge.svg)](https://github.com/ceezix-node/DNYFappbuilder/releases)
[![Pages](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/pages.yml/badge.svg)](https://ceezix-node.github.io/DNYFappbuilder/)
[![License: MIT](https://img.shields.io/badge/License-MIT-6C63FF.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Termux-0D1117?logo=linux&logoColor=white)](https://github.com/ceezix-node/DNYFappbuilder)
[![Templates](https://img.shields.io/badge/Templates-14-6C63FF)](#-templates)
[![Tests](https://img.shields.io/badge/Tests-18%2F18%20passing-00d4aa)](https://github.com/ceezix-node/DNYFappbuilder/actions)
[![Homebrew](https://img.shields.io/badge/Homebrew-tap%20available-FBB040?logo=homebrew&logoColor=white)](https://github.com/ceezix-node/homebrew-tap)
[![Made by ceezix-node](https://img.shields.io/badge/Built%20by-ceezix--node-6C63FF)](https://github.com/ceezix-node)

**[🌐 Live Site](https://ceezix-node.github.io/DNYFappbuilder/) · [📖 Docs](https://ceezix-node.github.io/DNYFappbuilder/docs/) · [📦 Releases](https://github.com/ceezix-node/DNYFappbuilder/releases) · [🐛 Issues](https://github.com/ceezix-node/DNYFappbuilder/issues)**

</div>

---

## ◈ What is DNYFappbuilder?

A single command-line tool that replaces an entire toolchain. It **detects** your project type automatically, **builds** it for any target, **signs** the output for release, **installs** it directly to a connected device, and **deploys** it to the cloud — all without you touching Gradle, Xcode, webpack configs, or platform-specific CLIs.

Built to run **natively on Android via Termux** — no root, no laptop required. It's the only production build system that behaves identically on your phone, your laptop, and your CI server.

```
SYSTEM STATUS ───────────────────────────────────────────────
  Build Engine     ████████████████████  ONLINE
  Device Layer     ████████████████████  ONLINE
  Signing Module   ████████████████████  ONLINE
  Deploy Grid      ████████████████████  ONLINE   6 targets
  Plugin Runtime   ████████████████████  ONLINE   3 plugins
  Template Engine  ████████████████████  ONLINE  14 stacks
───────────────────────────────────────── DNYFappbuilder v2.2.0
```

---

## ◈ Install

**One-liner — Linux / macOS / Termux**
```bash
curl -fsSL https://raw.githubusercontent.com/ceezix-node/DNYFappbuilder/main/install.sh | bash
```

**Homebrew — macOS / Linux**
```bash
brew tap ceezix-node/tap
brew install abp
```

**Termux on Android — no root required**
```bash
termux-setup-storage
pkg install git curl
curl -fsSL https://raw.githubusercontent.com/ceezix-node/DNYFappbuilder/main/install.sh | bash
```

**Manual**
```bash
git clone https://github.com/ceezix-node/DNYFappbuilder.git ~/dnyf-appbuilder
cd ~/dnyf-appbuilder && ./setup.sh
source ~/.bashrc
```

**Verify + auto-fix missing tools**
```bash
abp doctor --fix
```

---

## ◈ Quick Start

```bash
# One pipeline: scaffold → build → sign → install
abp init myapp flutter
abp build myapp --target android --profile release --sign --install

# Ship to the cloud
abp deploy railway

# Install wirelessly via QR code — no USB needed
abp install myapp.apk --qr
```

---

## ◈ Why DNYFappbuilder

| | Traditional toolchain | DNYFappbuilder |
|---|---|---|
| Setup | Install Gradle, Xcode CLI, Android SDK manually | `abp doctor --fix` — one command |
| Build | Different command per framework | `abp build` — auto-detects everything |
| Sign | `keytool`, `jarsigner`, `apksigner` separately | `abp sign --auto` |
| Install | Drag/drop, ADB commands, cables | `abp install --qr` — scan and done |
| Deploy | Platform-specific CLIs and configs | `abp deploy <target>` — same syntax everywhere |
| Mobile dev | Requires a laptop | Runs natively on **Termux** |

---

## ◈ Templates

**14 production-ready scaffolds — zero placeholder code:**

| Template | Stack | Output |
|---|---|---|
| `react-native` | TypeScript | Android APK · iOS IPA |
| `flutter` | Dart | Android · iOS · Web |
| `android` | Kotlin (Gradle DSL) | Android APK |
| `nodejs` | Express + Helmet + Morgan | Server |
| `nodejs-ts` | TypeScript + Express | Server |
| `python` | FastAPI + SQLAlchemy + Alembic | Server |
| `django` | Django REST Framework + CORS | Server |
| `java` | Spring Boot 3 | JAR |
| `go` | Chi router + Makefile | Binary |
| `rust` | Actix-Web 4 | Binary |
| `react` | Vite — fully scaffolded, no network needed | Web bundle |
| `vue` | Vite + Pinia + Router | Web bundle |
| `nextjs` | Next.js 14 App Router + API routes | Web app |
| `svelte` | SvelteKit + Vite | Web app |
| `electron` | Secure preload + context isolation | Desktop app |
| `pwa` | Vite PWA plugin + offline service worker | Installable web app |

```bash
abp init myapi nodejs-ts
abp init dashboard nextjs
abp init desktop-tool electron
```

---

## ◈ Command Reference

### Project
```bash
abp init <name> <template>             # Scaffold from 14 templates
abp build <path> [flags]               # Auto-detecting build
abp clean [path]                       # Clear cache + artifacts
```

### Device Intelligence
```bash
abp devices                            # List connected devices (USB)
abp devices --wireless                 # Scan WiFi ADB devices
abp install <app.apk>                  # Auto-select device
abp install <app.apk> --all            # Install to every connected device
abp install <app.apk> --wireless <ip>  # WiFi ADB — no cable
abp install <app.apk> --qr             # QR code wireless install
abp install <app.apk> --verify         # Install + confirm package registered
abp uninstall <com.package.id>         # Remove from device(s)
abp screenshot                         # Capture device screen
abp logcat                             # Stream live device logs
```

### Signing
```bash
abp keygen                             # Generate keystore + print CI secrets
abp sign <app.apk> --auto              # Auto-sign (generates key if missing)
abp verify-sign <app.apk>              # Verify signature integrity
```

### Deploy Grid
```bash
abp deploy render                      # Render.com
abp deploy railway                     # Railway.app
abp deploy vercel                      # Vercel
abp deploy heroku                      # Heroku
abp deploy docker <image>              # Docker registry
abp deploy github-pages                # GitHub Pages
```

### System
```bash
abp doctor                             # Environment scan
abp doctor --fix                       # Auto-install every missing tool
abp env create <name>                  # Environment profile manager
abp plugins list                       # Manage plugins
abp update                             # Self-update from GitHub
abp version                            # Version + runtime info
```

### Build Flags
```bash
--target   android | ios | web | all
--profile  debug | release | staging
--parallel              # Build all targets simultaneously
--sign --install        # One-shot release pipeline
--notify                 # Push notification on completion
--no-cache               # Bypass build cache
```

---

## ◈ Auto-Fix Environment

`abp doctor --fix` detects your package manager (Termux/apt/brew/dnf/pacman) and installs every missing tool — Node, Python, Java, ADB, Docker, qrencode, and more — in one shot.

```bash
abp doctor --fix
```
```
DNYFappbuilder — Doctor v2.2.0
Auto-fix mode enabled

Core Tools          ✓✓✓✓
Build Runtimes       ✓✓✓✓✓⚠⚠⚠
Android Tools        ✓⚠⚠✓⚠
Installing 6 missing tool(s) via: apt
  Installing Flutter         ... ✓ done
  Installing Gradle          ... ✓ done
  ...
✓ Environment fully configured!
```

---

## ◈ CI/CD Pipeline

**6-job GitHub Actions pipeline, runs on every push:**

```
BUILD & TEST ────────────────────────────────────────────────
  ✦ Test CLI              18-test suite — version, init, build, devices, env
  ✦ Build Node.js         Compiles + smoke-tests examples/nodejs-api
  ✦ Build Python          Compiles + smoke-tests examples/python-api
  ✦ Build Docker Images   Multi-stage builds, container health checks
  ✦ Validate Flutter      pub get · analyze · test
  ✦ Validate React Native npm install · TypeScript check

RELEASE  (on push to main + version tags) ───────────────────
  ✦ Auto-versions from date + commit SHA (pre-release)
  ✦ Full release on git tag push (e.g. v2.2.0)
  ✦ Generates changelog from commit history
  ✦ Publishes tarball + install instructions

PAGES  (on push to main) ─────────────────────────────────────
  ✦ Deploys landing page + docs to GitHub Pages
  ✦ Live at ceezix-node.github.io/DNYFappbuilder
```

---

## ◈ Plugin System

```bash
abp plugins list
abp plugins install <name>
abp plugins remove <name>
```

| Plugin | Function |
|---|---|
| `qr-installer` | Serves APK via HTTP + generates scannable QR for wireless install |
| `gradle-optimizer` | Tunes Gradle daemon memory, parallelism, and build cache |
| `npm-security` | Runs `npm audit` before every JS build, blocks on critical CVEs |

---

## ◈ Docker

```bash
docker build -f docker/nodejs.Dockerfile  -t myapp:latest .
docker build -f docker/python.Dockerfile  -t myapi:latest .
docker build -f docker/android.Dockerfile -t android-builder:latest .
docker build -f docker/flutter.Dockerfile -t flutter-builder:latest .
docker compose up -d
```

Every image: multi-stage build · non-root runtime · health checks · Alpine/slim base.

---

## ◈ Kubernetes

```bash
kubectl apply -f k8s/deployment.yml
```
Includes `Deployment`, `Service`, `Ingress` with resource limits and liveness probes.

---

## ◈ Requirements

| Tool | Purpose | Install |
|---|---|---|
| `bash 5+` | Runtime | Pre-installed |
| `git` | Source control | `pkg install git` |
| `node` + `npm` | JS/TS projects | `pkg install nodejs` |
| `python3` | Python projects | `pkg install python` |
| `java` JDK 17+ | Android/Spring Boot | `pkg install openjdk-17` |
| `flutter` | Flutter projects | [flutter.dev](https://flutter.dev) |
| `go` | Go projects | `pkg install golang` |
| `cargo` | Rust projects | [rustup.rs](https://rustup.rs) |
| `adb` | Device install | `pkg install android-tools` |
| `docker` | Containers | [docker.com](https://docker.com) |
| `qrencode` | QR install | `pkg install qrencode` |

> Every dependency is **optional**. DNYFappbuilder only activates what your project needs. Run `abp doctor --fix` and stop worrying about setup.

---

## ◈ Signing in CI

Add repository secrets and every release tag gets a signed APK automatically:

```
Settings → Secrets → Actions
KEYSTORE_BASE64 · KEY_ALIAS · KEY_PASSWORD · STORE_PASSWORD
```

```bash
abp keygen    # generates keystore + prints all 4 secret values ready to paste
```

→ [Full signing setup guide](docs/signing-secrets.md)

---

## ◈ Repository Activity

```
RELEASE LOG ─────────────────────────────────────────────────

  v2.2.0  ·  2025
           ·  8 new templates: nextjs, svelte, electron, nodejs-ts,
              django, go, pwa, rust
           ·  React + Vue fully scaffolded — zero network dependency
           ·  abp doctor --fix — auto-installs missing tools
           ·  CI signing pipeline with GitHub secrets
           ·  Homebrew tap: brew install abp
           ·  AI audio broadcast — listen to the overview
           ·  18/18 automated tests passing
           ·  Auto-release on every push to main

  v2.0.0  ·  2025
           ·  Device install engine — USB · WiFi · QR
           ·  APK signing pipeline
           ·  6 cloud deploy targets
           ·  Plugin system + Kubernetes manifests
           ·  Full CI — 6 GitHub Actions jobs

  v1.0.0  ·  2024
           ·  Initial release — core build system

─────────────────────────────────────────────────────────────
```

---

## ◈ License

```
MIT License — Copyright © 2025 ceezix-node
Free to use, modify, and distribute with attribution.
```

---

<div align="center">

**[ceezix-node](https://github.com/ceezix-node)** · Built for builders who move fast

`abp doctor --fix` — start here

</div>
