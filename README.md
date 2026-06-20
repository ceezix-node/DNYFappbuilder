<div align="center">

 █████╗  ██████╗  ██████╗
██╔══██╗ ██╔══██╗ ██╔══██╗
███████║ ██████╔╝ ██████╔╝
██╔══██║ ██╔══██╗ ██╔═══╝
██║  ██║ ██████╔╝ ██║
╚═╝  ╚═╝ ╚═════╝  ╚═╝

### `ceezix-node v2.0.0`
**Autonomous Multi-Language Build Intelligence**

*Build · Sign · Install · Deploy — from a single command*

---

[![Build & Test](https://github.com/ceezix-node/ceezix-node/actions/workflows/build.yml/badge.svg)](https://github.com/ceezix-node/ceezix-node/actions/workflows/build.yml)
[![Release](https://github.com/ceezix-node/ceezix-node/actions/workflows/release.yml/badge.svg)](https://github.com/ceezix-node/ceezix-node/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-6C63FF.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Termux-0D1117?logo=linux&logoColor=white)](https://github.com/ceezix-node/ceezix-node)
[![Shell](https://img.shields.io/badge/Shell-Bash%205%2B-4EAA25?logo=gnubash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Templates](https://img.shields.io/badge/Templates-8%20Supported-blue)](https://github.com/ceezix-node/ceezix-node#-templates)
[![Made by ceezix-node](https://img.shields.io/badge/Made%20by-ceezix-node-6C63FF)](https://github.com/ceezix-node)

</div>

---

## ◈ Overview

**ceezix-node** is a production-grade, autonomous build system engineered for developers who demand precision, speed, and full pipeline control. It detects your project type, orchestrates the full build lifecycle, signs your output, deploys it to connected devices or cloud targets — and notifies you when done. One CLI. Zero friction.

Designed to operate natively in **Termux on Android**, as well as Linux and macOS environments — making it the only build system that runs on your phone, your laptop, and your server with identical behavior.

SYSTEM ONLINE ──────────────────────────────────────────────
  Build Engine    ████████████████████  READY
  Device Layer    ████████████████████  READY
  Sign Module     ████████████████████  READY
  Deploy Grid     ████████████████████  READY
  Plugin Runtime  ████████████████████  READY
─────────────────────────────────────── ceezix-node v2.0.0

---

## ◈ Install

### One-liner — Linux / macOS / Termux

```bash
curl -fsSL https://raw.githubusercontent.com/ceezix-node/ceezix-node/main/install.sh | bash

Termux on Android — no root required

pkg install git curl
curl -fsSL https://raw.githubusercontent.com/ceezix-node/ceezix-node/main/install.sh | bash

Manual

git clone https://github.com/ceezix-node/ceezix-node.git ~/ceezix-node
cd ~/ceezix-node && ./setup.sh
source ~/.bashrc

Verify installation

abp doctor

◈ Quick Start

abp init myapp flutter
abp build myapp --target android --profile release --sign --install

abp deploy railway

abp install myapp.apk --qr

◈ System Architecture

ceezix-node/ceezix-node
│
├── bin/abp
├── lib/
├── scripts/
├── docker/
├── examples/
├── plugins/
├── tests/
├── k8s/
├── setup.sh
└── install.sh

◈ Command Reference

Project

abp init <name> <template>
abp build <path> [options]
abp clean [path]

Device Intelligence

abp devices
abp devices --wireless
abp install <app.apk>
abp install <app.apk> --all
abp install <app.apk> --wireless <ip>
abp install <app.apk> --qr
abp install <app.apk> --verify
abp uninstall <com.package.id>
abp screenshot
abp logcat

Signing Pipeline

abp keygen
abp sign <app.apk> --auto
abp sign <app.apk> --keystore <path>
abp verify-sign <app.apk>

Deploy Grid

abp deploy render
abp deploy railway
abp deploy vercel
abp deploy heroku
abp deploy docker <image>
abp deploy github-pages

System Utilities

abp doctor
abp logs [--tail N]
abp env create <name>
abp env list
abp env apply <name> [dir]
abp env show <name>
abp plugins list
abp update
abp version

◈ Templates

Template

Language

Output

react-native

TypeScript

Android APK · iOS IPA

flutter

Dart

Android · iOS · Web

android

Kotlin

Android APK

nodejs

JavaScript

Server

python

Python

Server

java

Java

JAR / WAR

react

JavaScript

Web

vue

JavaScript

Web

◈ CI/CD Pipeline

ceezix-node ships with a full GitHub Actions pipeline across 6 automated jobs.

BUILD & TEST PIPELINE

Test CLI

Build Node.js

Build Python

Build Docker Images

Validate Flutter

Validate React Native

RELEASE PIPELINE

Auto changelog generation

Versioned release packages

GitHub Release publishing

◈ Plugin System

abp plugins list
abp plugins install <name>
abp plugins remove <name>

Bundled plugins:

qr-installer

gradle-optimizer

npm-security

◈ Docker

docker build -f docker/nodejs.Dockerfile -t myapp:latest .
docker build -f docker/python.Dockerfile -t myapi:latest .
docker build -f docker/android.Dockerfile -t android-builder:latest .
docker build -f docker/flutter.Dockerfile -t flutter-builder:latest .

docker compose up -d

◈ Environment Profiles

abp env create production
abp env create staging
abp env list
abp env apply production ./myapp
abp env show production
abp env delete staging

◈ Kubernetes

kubectl apply -f k8s/deployment.yml

◈ Requirements

Dependency

Purpose

bash 5+

Runtime

git

Source Control

node + npm

JavaScript Builds

python3 + pip

Python Builds

OpenJDK 17+

Android / Java

flutter

Flutter

adb

Device Deployment

docker

Containers

qrencode

QR Install

All dependencies are optional. ceezix-node automatically activates only the tools required for the detected project.

◈ Repository Activity

RELEASE LOG ────────────────────────────────────────────────

v2.0.0

Complete rewrite

Device install engine

APK signing pipeline

6 cloud deploy targets

8 project templates

5 production Dockerfiles

4 example projects

3 bundled plugins

Full CI pipeline

Kubernetes manifests

Termux-native support

v1.0.0

Initial release

Core build system

Node.js + Python templates

─────────────────────────────────────────────────────────────

◈ License

MIT License — Copyright © 2026 ceezix-node

Free to use, modify, and distribute with attribution.

https://github.com/ceezix-node

Built for builders who move fast.

abp doctor — start here
