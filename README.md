<div align="center">

# 🚦 Smart Traffic AI Dashboard

**A Reinforcement Learning–powered traffic signal optimization simulator**  
Built as a single, zero-dependency `index.html` file.

[![Status](https://img.shields.io/badge/status-live-00e5c8?style=flat-square)](#)
[![Tech](https://img.shields.io/badge/built%20with-vanilla%20JS-f59e0b?style=flat-square)](#)
[![Chart](https://img.shields.io/badge/chart-Chart.js%204.4-3b82f6?style=flat-square)](#)
[![License](https://img.shields.io/badge/license-MIT-7c3aed?style=flat-square)](#license)

</div>

---

## 📸 Overview

> A production-quality dashboard that simulates how a Reinforcement Learning agent learns to optimize urban traffic signals in real time. Every metric, chart, and signal light updates live — no backend, no build step, no dependencies to install.

The simulation models the classic **traffic signal control problem**: minimize vehicle queue length and average wait time by learning an optimal switching policy across Red → Yellow → Green cycles. The RL agent uses a PPO-style reward function that scores each state based on throughput gain, wait penalty, and phase-appropriate bonuses.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎯 **RL Reward Engine** | Reward computed per step from throughput, wait penalty & phase bonus |
| 🚗 **Vehicle Queue Simulation** | Realistic random-walk model biased by current signal phase |
| ⏱ **Wait Time Dynamics** | Per-vehicle avg wait drifts with queue size and signal state |
| 🚦 **Animated Signal Light** | Full Red → Yellow → Green cycle with per-phase countdown timers |
| 📈 **Live Multi-Series Chart** | Rolling 60-step history — Reward, Vehicles, Wait on dual Y-axes |
| 📋 **Event Log** | Color-coded live feed of phase changes, congestion alerts, reward spikes |
| 📊 **Trend Indicators** | Per-card ↑ / ↓ badges with % change vs previous step |
| 🎨 **SaaS Dark UI** | Animated grid, ambient blobs, Space Grotesk + JetBrains Mono fonts |

---

## 🚀 Getting Started

No installation. No npm. No server.

```bash
# 1. Clone or download
git clone https://github.com/your-username/smart-traffic-ai-dashboard.git

# 2. Open in browser
open index.html
```

Or just **drag `index.html` into any browser tab** and click **▶ Start Simulation**.

---

## 🧠 How the Simulation Works

### Signal Phase Cycle

```
RED (12s) ──▶ YELLOW (3s) ──▶ GREEN (10s) ──▶ RED ...
```

Each phase influences vehicle accumulation and wait time through a weighted drift model:

| Phase  | Vehicle Target | Wait Target | Effect |
|--------|---------------|-------------|--------|
| 🔴 RED    | ~70 vehicles  | ~40s        | Queue builds |
| 🟡 YELLOW | ~50 vehicles  | ~22s        | Transition |
| 🟢 GREEN  | ~15 vehicles  | ~5s         | Queue clears |

### Reward Function

```
reward = throughput_bonus
       - wait_penalty
       + phase_bonus
       + noise

where:
  throughput_bonus = (100 - vehicles) × 0.6   // reward clearing traffic
  wait_penalty     = wait_time × 0.5           // penalize long queues
  phase_bonus      = +15 (GREEN), -10 (RED)    // signal-aware shaping
  noise            = uniform(-6, +6)           // environment stochasticity
```

Reward range: approximately **−50 to +100** per step.

---

## 🗂 Project Structure

```
smart-traffic-ai-dashboard/
└── index.html        ← entire application (HTML + CSS + JS)
└── README.md         ← you are here
```

---

## 🎛 Dashboard Controls

| Button | Action |
|--------|--------|
| **▶ Start Simulation** | Begins the 1-second tick loop |
| **■ Stop** | Pauses at the current step (state preserved) |
| **↺ Reset** | Clears all data and returns to idle state |

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Markup | Semantic HTML5 |
| Styling | Vanilla CSS (custom properties, grid, flexbox, keyframes) |
| Logic | Vanilla JavaScript (ES2020) |
| Charts | [Chart.js 4.4](https://www.chartjs.org/) via CDN |
| Fonts | [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts |

No frameworks. No bundlers. No runtime dependencies.

---
