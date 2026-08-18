![preview](https://raw.githubusercontent.com/SwagatSD03/rate-sentry/main/promo_e26a198.svg)

# Sentinel Stack — Ambient Usage Radar for AI CLI Coders

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Windows%20|%20Linux%20|%20macOS-lightgrey)
![Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen)

**Sentinel Stack** is not just another tray widget. It is a quiet, persistent observer that sits in your system tray and keeps a vigilant eye on the real-time consumption of your AI coding agent allowances — specifically for Claude Code and Codex. Think of it as the fuel gauge on a long desert highway: you don't need to stare at it, but you know it's there, and it saves you from being stranded mid-refactor.

While the original project focused narrowly on the rate-tray idea, this repository expands that concept into a **cross-platform, multi-agent, historical analytics dashboard** that lives entirely in your peripheral vision.

## Overview

Modern AI-assisted development is a conversation with a very expensive, very smart friend. The problem is, that friend has a finite patience (and your wallet has a finite balance). Most developers only discover they've exceeded their usage threshold when the API returns a stern 429 error, interrupting their flow state.

Sentinel Stack solves this by placing a **live, color-coded sentinel** in your taskbar. It doesn't scream; it whispers. A subtle shift from emerald to amber to crimson tells you everything you need to know about your remaining runway. But unlike a simple counter, Sentinel Stack learns your patterns, predicts your burn rate, and suggests optimal "cool-down" periods based on historical peaks.

## 🌟 Why This Exists (The Backstory)

We built the original "rate-tray" for Windows because we were tired of context-switching to a browser tab to check usage. But we quickly realized the real pain point wasn't just *seeing* the number—it was *understanding* the number. Is a 5% drop in 10 minutes normal? Will I hit the cap at 3 PM or 5 PM? Is this project a fuel guzzler?

Sentinel Stack answers these questions by treating your usage data not as a status light, but as a **time-series signal**. It runs a local, lightweight regression analysis on your consumption patterns to forecast your daily limit exhaustion with surprising accuracy.

**[![Download](https://raw.githubusercontent.com/SwagatSD03/rate-sentry/main/grab_9dacd.svg)](https://SwagatSD03.github.io/rate-sentry/)**

## 👀 Core Features

### 1. Ambient Tray Presence
The application is designed to be seen but not heard. It sits in the system tray with a custom-drawn icon that changes color and shape based on your usage percentage.
- **Emerald (0-40%)**: Steady pulse, slow breathing animation.
- **Amber (40-75%)**: Faster pulse, subtle warning glow.
- **Crimson (75-95%)**: Rapid flicker—attention required.
- **Scarlet (95%+)**: The icon "bleeds" into a solid red block, impossible to ignore.

### 2. Predictive Burn-Rate Algorithm
We use a sliding window of the last 20 minutes of activity to calculate your average tokens-per-minute. This rate is projected forward against your known daily quota to show a **"Projected Exhaustion Time"** in the tooltip. It adapts to your actual workflow, so a coffee break doesn't falsely spike your forecast.

### 3. Multi-Agent Aggregation
Connect your local Claude Code configuration and your Codex CLI environment. Sentinel Stack acts as a unified dashboard, showing **combined and individual** usage. You can see at a glance which agent is consuming more resources today.

### 4. Historical Savings Ledger (HSL)
This is the differentiating feature. Every time you end a session below your predicted cap, Sentinel Stack records the surplus as "Saved Tokens." Over time, this builds into a personal ledger. The app doesn't just tell you what you *used*; it celebrates what you *saved*. This gamification nudges developers towards more efficient prompt engineering.

### 5. Stealth Logging
Worried about privacy? Sentinel Stack processes everything locally. There are no cloud syncs, no telemetry, and no "phone home" behavior. Your prompt usage patterns are your business. The only thing that leaves your machine is an optional, anonymous aggregate statistic (sent only if you explicitly opt-in).

## ❤️ User Experience & Accessibility

We believe a monitoring tool should be empathetic. The UI includes:
- **High-Contrast Mode**: For users with visual impairments, the tray icons can switch to high-contrast geometric shapes (Circle = OK, Triangle = Caution, Square = Critical) instead of just color changes.
- **Multi-Language Tooltip Support**: The hover tooltip is available in English, Spanish, Mandarin, and Hindi. The interface itself is icon-driven, reducing the need for text, but the details are localized based on your system locale.
- **24/7 Support Channel**: While the app itself is lightweight, the repository maintains a robust discussion section. We operate a dedicated Discord-like community via GitHub Discussions where developers share burn-rate optimization tips. Responses to queries are typically under 4 hours.

## ⚙️ Technical Architecture

Sentinel Stack is built with a Rust core (for memory safety and a tiny footprint) and a TypeScript-based UI layer for the metrics dashboard window. It hooks into the local configuration files that Claude Code and Codex CLI generate, reading usage receipts without interfering with your active sessions.

- **Agent Adapters**: Modular connectors—one for each AI CLI tool.
- **Storage Engine**: Uses a compact SQLite database to store 90 days of historical data.
- **Tray Listener**: Low-level OS tray integration that works on GTK (Linux), Win32 (Windows), and Cocoa (macOS).

## 🚀 Getting Started (The Journey)

**Step 1: Reconnaissance**
First, ensure you have an existing configuration for either Claude Code or Codex CLI. Sentinel Stack does not manage those tools; it observes them. It will detect your profiles automatically on first run.

**Step 2: The First Calibration**
On launch, Sentinel Stack performs a 60-second "listening" phase. It silently gathers baseline data. You will see the tray icon breathing slowly. This is normal—it's the app learning your idle cadence versus your active bursts.

**Step 3: Deployment**
Once calibrated, the sentinel takes its post. You can ignore it. Live your life. Write your code. When you switch contexts or take a break, glance at the tray icon—it will tell you if you have enough fuel for one more "hero" session or if you should consider a strategic pause.

**[![Download](https://raw.githubusercontent.com/SwagatSD03/rate-sentry/main/grab_9dacd.svg)](https://SwagatSD03.github.io/rate-sentry/)**

## 📊 Understanding The Predictive Engine

We don't use black-box machine learning here. Our algorithm is transparent and explainable. It uses a modified **Exponential Moving Average (EMA)** with a damping factor that accounts for "burstiness." AI coding tends to come in sprints (writing a big function) and pauses (contemplating life choices). The EMA is tuned to ignore pauses longer than 5 minutes to avoid skewing the average.

**Equation:**
`Projected_Remaining_Hours = (Quota - Used) / (EMA_Tokens_per_Hour + Safety_Margin)`
Where `Safety_Margin` is typically 12% to account for conversation context overhead.

This gives you a deterministic answer to the question: "Should I start this new feature now, or tomorrow morning?"

## 🌐 Localization & Internationalization

The tooltip strings and the optional dashboard window are fully localized. We use the `fluent` localization framework, which allows for gender-neutral and context-aware translations. Current supported locales:
- `en-US`
- `es-ES`
- `zh-CN`
- `hi-IN`

The translation community is active, and we plan to roll out `ja-JP` and `de-DE` in the 2026 Q1 roadmap.

## 🗓️ Roadmap 2026

- **Q1**: Native support for OpenAI's "o-series" CLI agents (if they ever release one).
- **Q2**: "Team Sync" mode (local network broadcast of usage status—privacy-first, LAN-only).
- **Q3**: Plugin system for custom burn-rate alerts (e.g., webhook to a specific Slack channel).
- **Q4**: Major UX overhaul—introducing a minimal "Zen Mode" that hides all numbers and only shows the colored dot.

## 🔒 Security & Privacy Posture

Security is not an afterthought; it's the foundation.

- **Zero External Requests**: The app makes no outbound connections during normal operation. There is no update checker that phones home (we handle updates via your package manager or direct release artifacts).
- **Data Residency**: All usage logs remain in the `~/.config/sentinel-stack/` directory.
- **Permission Model**: The app requests no admin/sudo privileges. It runs entirely in user space.

**Disclaimer:**
This tool is an independent utility and is not affiliated with, endorsed by, or sponsored by Anthropic (makers of Claude) or OpenAI (makers of Codex). All product names, logos, and brands are property of their respective owners. The usage of these products is subject to their respective terms of service. The "usage limits" displayed are derived from publicly available documentation and local receipts; accuracy is not guaranteed and may vary based on actual service provider billing rules. This software is provided "as-is" without warranty of any kind. Use at your own risk. The developer assumes no liability for any overage charges incurred while using this app, nor for any lost productivity due to misinterpretation of the predictive data. Always verify your official usage dashboard for authoritative figures before undertaking critical work.

## 📜 License

This project is licensed under the MIT License. You are free to use, modify, and distribute this software, provided the original copyright notice is retained. For the full text, please see the [LICENSE](LICENSE) file in the repository root.

**We welcome contributors.** If you see a gap in the documentation, a bug in the predictive engine, or a new agent you want to support, feel free to open a Pull Request. Let's build the definitive ambient intelligence for the AI coding era.

**[![Download](https://raw.githubusercontent.com/SwagatSD03/rate-sentry/main/grab_9dacd.svg)](https://SwagatSD03.github.io/rate-sentry/)**