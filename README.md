<div align="center">

```
 █████╗  ██████╗  ██████╗ 
██╔══██╗ ██╔══██╗ ██╔══██╗
███████║ ██████╔╝ ██████╔╝
██╔══██║ ██╔══██╗ ██╔═══╝ 
██║  ██║ ██████╔╝ ██║     
╚═╝  ╚═╝ ╚═════╝  ╚═╝     
```

### `DNYFappbuilder v2.0.0`
**Autonomous Multi-Language Build Intelligence**

*Build · Sign · Install · Deploy — from a single command*

---

[![Build & Test](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/build.yml/badge.svg)](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/build.yml)
[![Release](https://github.com/ceezix-node/DNYFappbuilder/actions/workflows/release.yml/badge.svg)](https://github.com/ceezix-node/DNYFappbuilder/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-6C63FF.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Termux-0D1117?logo=linux&logoColor=white)](https://github.com/ceezix-node/DNYFappbuilder)
[![Shell](https://img.shields.io/badge/Shell-Bash%205%2B-4EAA25?logo=gnubash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Templates](https://img.shields.io/badge/Templates-8%20Supported-blue)](https://github.com/ceezix-node/DNYFappbuilder#-templates)
[![Made by ceezix-node](https://img.shields.io/badge/Made%20by-ceezix-node-6C63FF)](https://github.com/ceezix-node)

</div>

---

## ◈ Overview

**DNYFappbuilder** is a production-grade, autonomous build system engineered for developers who demand precision, speed, and full pipeline control. It detects your project type, orchestrates the full build lifecycle, signs your output, deploys it to connected devices or cloud targets — and notifies you when done. One CLI. Zero friction.

Designed to operate natively in **Termux on Android**, as well as Linux and macOS environments — making it the only build system that runs on your phone, your laptop, and your server with identical behavior.

```
SYSTEM ONLINE ──────────────────────────────────────────────
  Build Engine    ████████████████████  READY
  Device Layer    ████████████████████  READY
  Sign Module     ████████████████████  READY
  Deploy Grid     ████████████████████  READY
  Plugin Runtime  ████████████████████  READY
─────────────────────────────────────── DNYFappbuilder v1.0.0
```

---

## ◈ Install

**One-liner — Linux / macOS / Termux**
```bash
curl -fsSL https://raw.githubusercontent.com/ceezix-node/DNYFappbuilder/main/install.sh | bash
```

**Termux on Android — no root required**
```bash
pkg install git curl
curl -fsSL https://raw.githubusercontent.com/ceezix-node/DNYFappbuilder/main/install.sh | bash
```

**Manual**
```bash
git clone https://github.com/ceezix-node/DNYFappbuilder.git ~/dnyf-appbuilder
cd ~/dnyf-appbuilder && ./setup.sh
source ~/.bashrc
```

**Verify installation**
```bash
abp doctor
```

---

## ◈ Quick Start

```bash
# Initialize → Build → Sign → Install in one pipeline
abp init myapp flutter
abp build myapp --target android --profile release --sign --install

# Deploy to cloud instantly
abp deploy railway

# Wireless install via QR code — no USB needed
abp install myapp.apk --qr
```

---

## ◈ System Architecture

```
ceezix-node/DNYFappbuilder
│
├── bin/abp                      ← CLI entry point — all commands routed here
│
├── lib/                         ← Core intelligence modules
│   ├── common.sh                │  Logging, color system, shared utilities
│   ├── detect.sh                │  Auto-detects project type (8 frameworks)
│   ├── devices.sh               │  ADB + iOS device management layer
│   ├── install.sh               │  APK/IPA installation engine
│   ├── signing.sh               │  Keystore generation + APK signing
│   └── notify.sh                │  Termux + Slack + webhook notifications
│
├── scripts/                     ← Execution layer
│   ├── build.sh                 │  Multi-target parallel build orchestrator
│   ├── init.sh                  │  Project scaffolding (8 templates)
│   ├── install.sh               │  USB + WiFi + QR device deployment
│   ├── devices.sh               │  Device listing, battery, model detection
│   ├── sign.sh                  │  APK signing pipeline
│   ├── keygen.sh                │  Release keystore generator
│   ├── doctor.sh                │  Environment health diagnostics
│   ├── env.sh                   │  Environment profile manager
│   ├── update.sh                │  Self-update from GitHub
│   ├── deploy/                  │  Cloud deployment targets (6 platforms)
│   └── completions/             │  Bash + Zsh tab completion
│
├── docker/                      ← Production container definitions
│   ├── nodejs.Dockerfile        │  Node.js multi-stage (Alpine)
│   ├── python.Dockerfile        │  Python 3.11 multi-stage (slim)
│   ├── android.Dockerfile       │  Android SDK + Gradle
│   ├── flutter.Dockerfile       │  Flutter SDK + Android tools
│   └── java.Dockerfile          │  OpenJDK 17 + Maven/Gradle
│
├── examples/                    ← Reference implementations
│   ├── nodejs-api/              │  Express REST API
│   ├── python-api/              │  FastAPI server
│   ├── flutter-app/             │  Cross-platform mobile app
│   └── react-native-app/        │  React Native TypeScript app
│
├── plugins/                     ← Extensible plugin system
│   ├── qr-installer/            │  QR-code wireless APK install
│   ├── gradle-optimizer/        │  Gradle build cache + speed tuning
│   └── npm-security/            │  npm audit + vulnerability scanner
│
├── tests/                       ← Full CI test suite — 9/9 passing
├── k8s/                         ← Kubernetes deployment manifests
├── setup.sh                     ← Local + CI installer
└── install.sh                   ← One-liner remote installer
```

---

## ◈ Command Reference

### Project
```bash
abp init <name> <template>             # Scaffold a new project
abp build <path> [options]             # Build application
abp clean [path]                       # Clear cache and build artifacts
```

### Device Intelligence
```bash
abp devices                            # Scan and list all connected devices
abp devices --wireless                 # Scan WiFi ADB devices on network
abp install <app.apk>                  # Auto-select device and install
abp install <app.apk> --all            # Broadcast install to all devices
abp install <app.apk> --wireless <ip>  # WiFi ADB install — no USB required
abp install <app.apk> --qr             # Serve APK + generate QR for install
abp install <app.apk> --verify        # Install + verify package is registered
abp uninstall <com.package.id>         # Remove app from device(s)
abp screenshot                         # Capture device screen to local file
abp logcat                             # Stream live device logs
```

### Signing Pipeline
```bash
abp keygen                             # Generate production release keystore
abp sign <app.apk> --auto             # Sign APK — auto-generates key if absent
abp sign <app.apk> --keystore <path>   # Sign with a specific keystore file
abp verify-sign <app.apk>             # Verify APK signature integrity
```

### Deploy Grid
```bash
abp deploy render                      # Deploy to Render.com
abp deploy railway                     # Deploy to Railway.app
abp deploy vercel                      # Deploy to Vercel
abp deploy heroku                      # Deploy to Heroku
abp deploy docker <image>              # Push to Docker registry
abp deploy github-pages                # Deploy static site to GitHub Pages
```

### System Utilities
```bash
abp doctor                             # Full environment diagnostics
abp logs [--tail N]                    # View build logs
abp env create <name>                  # Create environment profile
abp env list                           # List all profiles
abp env apply <name> [dir]             # Apply profile to project directory
abp env show <name>                    # Print profile contents
abp plugins list                       # List installed plugins
abp update                             # Self-update DNYFappbuilder from GitHub
abp version                            # Show version and runtime info
```

### Build Flags
```bash
--target   android | ios | web | all   # Target platform(s)
--profile  debug | release | staging   # Build profile
--parallel                             # Run all targets simultaneously
--sign                                 # Auto-sign output after build
--install                              # Deploy to device after build
--notify                               # Push notification on completion
--no-cache                             # Bypass build cache
--output <dir>                         # Custom output directory
```

---

## ◈ Templates

| Template | Language | Output | Framework |
|---|---|---|---|
| `react-native` | TypeScript | Android APK · iOS IPA | React Native 0.73 |
| `flutter` | Dart | Android APK · iOS · Web | Flutter 3.x |
| `android` | Kotlin | Android APK | Android SDK 34 |
| `nodejs` | JavaScript | Server | Express + Node.js |
| `python` | Python | Server | FastAPI + Uvicorn |
| `java` | Java | JAR / WAR | Spring Boot 3 |
| `react` | JavaScript | Web bundle | Vite + React 18 |
| `vue` | JavaScript | Web bundle | Vite + Vue 3 |

---

## ◈ CI/CD Pipeline

DNYFappbuilder ships with a full GitHub Actions pipeline across **6 automated jobs**:

```
BUILD & TEST PIPELINE  ─────────────────────────────────────
  ✦ Test CLI              Installs ABP · runs full 9-test suite
  ✦ Build Node.js         Compiles · verifies examples/nodejs-api
  ✦ Build Python          Compiles · verifies examples/python-api
  ✦ Build Docker Images   Builds · smoke-tests Node + Python containers
  ✦ Validate Flutter      pub get · analyze · test
  ✦ Validate React Native npm install · TypeScript check

RELEASE PIPELINE  (triggered on: push tag v*)  ─────────────
  ✦ Auto-generates changelog from commit history
  ✦ Packages versioned release tarball
  ✦ Publishes GitHub Release with one-liner install instructions
```

---

## ◈ Plugin System

Extend DNYFappbuilder with the built-in plugin runtime:

```bash
abp plugins list                       # Show installed plugins
abp plugins install <name>             # Install a plugin
abp plugins remove <name>              # Remove a plugin
```

**Bundled plugins:**

| Plugin | Function |
|---|---|
| `qr-installer` | Serves APK over HTTP and generates a scannable QR code for instant wireless install |
| `gradle-optimizer` | Tunes Gradle daemon memory, parallel execution, and build cache for faster Android builds |
| `npm-security` | Runs `npm audit` before every JS build and blocks on critical CVEs |

---

## ◈ Docker

Every major stack ships with a hardened, multi-stage production Dockerfile:

```bash
docker build -f docker/nodejs.Dockerfile  -t myapp:latest .
docker build -f docker/python.Dockerfile  -t myapi:latest .
docker build -f docker/android.Dockerfile -t android-builder:latest .
docker build -f docker/flutter.Dockerfile -t flutter-builder:latest .

# Orchestrate all services
docker compose up -d
```

All images use:
- **Multi-stage builds** — minimal final image size
- **Non-root runtime user** — security hardened
- **Health checks** — `/health` endpoint verified on startup
- **Alpine / slim base** — production-optimized layers

---

## ◈ Environment Profiles

Manage per-environment configuration without touching your codebase:

```bash
abp env create production              # Creates config/envs/production.env
abp env create staging
abp env list                           # Lists all profiles
abp env apply production ./myapp       # Writes .env to project directory
abp env show production                # Prints profile contents
abp env delete staging                 # Removes profile
```

---

## ◈ Kubernetes

A production-ready manifest is included for cloud-native deployment:

```bash
kubectl apply -f k8s/deployment.yml
```

Includes `Deployment`, `Service`, and `Ingress` with configurable replicas, resource limits, and liveness/readiness health probes.

---

## ◈ Requirements

| Dependency | Purpose | Install |
|---|---|---|
| `bash 5+` | Runtime | Pre-installed |
| `git` | Source control | `pkg install git` |
| `node` + `npm` | JS / React Native builds | `pkg install nodejs` |
| `python3` + `pip` | Python builds | `pkg install python` |
| `java` JDK 17+ | Android / Spring Boot | `pkg install openjdk-17` |
| `flutter` | Flutter builds | [flutter.dev](https://flutter.dev) |
| `adb` | Android device install | `pkg install android-tools` |
| `docker` | Container builds | [docker.com](https://docker.com) |
| `qrencode` | QR wireless install | `pkg install qrencode` |

> All dependencies are **optional** — DNYFappbuilder only activates what your specific project type needs. Run `abp doctor` for a complete environment scan and missing tool report.

---

## ◈ Repository Activity

```
RELEASE LOG ────────────────────────────────────────────────

  v2.0.0  ·  2025
           ·  Complete rewrite — 67 files · 10,000+ lines
           ·  Device install engine (USB · WiFi · QR)
           ·  APK signing pipeline + keystore generator
           ·  6 cloud deploy targets
           ·  8 project templates
           ·  5 production Dockerfiles
           ·  4 reference example projects
           ·  3 bundled plugins
           ·  Full CI pipeline — 6 GitHub Actions jobs
           ·  9/9 automated tests passing
           ·  Kubernetes manifests
           ·  Bash + Zsh tab completion
           ·  Termux-native support

  v1.0.0  ·  2024
           ·  Initial release — core build system
           ·  Basic init, build, docker, clean commands
           ·  Node.js + Python Docker templates

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

`abp doctor` — start here

</div>
