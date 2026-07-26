<div align="center">

# Kayala Rushikesh Goud

**AI / LLM Engineer** · Autonomous agent systems that verify their own work

[![Portfolio](https://img.shields.io/badge/Portfolio-minduni.netlify.app-0A0A0A?style=for-the-badge&logo=vercel&logoColor=white)](https://minduni.netlify.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/rushikesh-goud-572007384)
[![Email](https://img.shields.io/badge/Email-Reach_me-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:rushikeshgoud19@gmail.com)

<samp>CS @ BITS Pilani · Hyderabad, India · open to SDE / AI engineering roles</samp>

</div>

---

I build AI agent systems that run on real hardware and do real work — not demos. Mostly Python,
FastAPI and LLM orchestration, with a stubborn interest in making agents **verifiable**: systems
that *prove* what they did instead of claiming it. Most of what I know came from things breaking in
ways I didn't predict.

A theme runs through the work: **one model asserting something is not evidence.** Mizune diffs its
claims against ground-truth seals, Project Sovereign reaches decisions through multi-agent debate,
and the trading framework keeps the agent that *wants* a trade separate from the one that approves it.

---

## 🧰 Languages & Tools

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=flat-square&logo=nodedotjs&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white)

![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6F00?style=flat-square&logo=databricks&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

![OpenAI](https://img.shields.io/badge/LLM_APIs-412991?style=flat-square&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![YOLO](https://img.shields.io/badge/YOLOv8-00FFFF?style=flat-square&logo=yolo&logoColor=black)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![RaspberryPi](https://img.shields.io/badge/Raspberry_Pi-A22846?style=flat-square&logo=raspberrypi&logoColor=white)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)

</div>

---

## 🚀 Featured Work

### 🤖 [Mizune](https://github.com/rushikeshgoud19/MY-AI) — an autonomous AI assistant that runs 24/7 on one 898 MB VM

<table>
<tr><td><b>Median input tokens</b></td><td>8.3k → <b>5.2k</b> (−37%)</td></tr>
<tr><td><b>Average latency</b></td><td>18.2s → <b>6.3s</b> (−65%)</td></tr>
<tr><td><b>Inference spend</b></td><td><b>$0</b> — 7-provider failover across free tiers</td></tr>
<tr><td><b>Scale</b></td><td>~12.6k LOC · 96 commits · solo</td></tr>
</table>

A FastAPI/WebSocket brain on an Azure VM, a WhatsApp interface, an Android client that drives the
phone through a custom `AccessibilityService`, and a three-layer memory system with ChromaDB
semantic recall.

Building it was the easy part. Keeping it alive taught me the rest:

- **It verifies its own claims.** LLMs will confidently report doing things they didn't — mine
  reported scheduling a task that was never scheduled. Every action now writes a ground-truth
  record, and multi-step tasks must prove each step against real system state before advancing.
- **7-provider failover with per-key rotation** — when one provider hits its daily token cap
  *mid-request*, the call retries a sibling key before degrading.
- **An evaluation harness** scoring each provider on response fidelity and tool-selection
  correctness, plus cross-model verification: a *different* model checks the answer than produced it.
- **The bug I'm fondest of:** it kept crashing, and I traced it to ~90 orphaned X11 display servers
  leaked one per restart over 18 days. My own watchdog was causing the crashes it existed to prevent.

`Python` `FastAPI` `WebSocket` `Azure` `Kotlin/Android` `ChromaDB` `Linux`

---

### 🌱 Open source — [traceroot-ai/traceroot](https://github.com/traceroot-ai/traceroot)

LLM observability platform. My most useful contribution wasn't a feature — it was noticing that the
same `$0`-cost bug had been patched **five separate times**.

| | |
|---|---|
| [**#1597**](https://github.com/traceroot-ai/traceroot/issues/1597) | Root cause: price resolution implemented twice (Python + TypeScript), no shared contract, no test that the shipped catalog resolves |
| [**#1619**](https://github.com/traceroot-ai/traceroot/pull/1619) | The fix: one resolution contract on both sides, most-specific-match ranking, catalog invariant tests → gateway-prefixed model IDs **5/160 → 356/356** |
| [**#1283**](https://github.com/traceroot-ai/traceroot/pull/1283) | Pre-merge row dedup in a ClickHouse `ReplacingMergeTree` query |
| [**#1330**](https://github.com/traceroot-ai/traceroot/pull/1330) | Model-selection persistence in the dashboard UI |

---

### 🏛️ [Project Sovereign](https://github.com/rushikeshgoud19/IBM-Project) — an autonomous AI boardroom

Multi-agent debate for supply-chain decisions on **IBM watsonx / Granite**. Specialist agents argue
opposing positions and a decision emerges from the disagreement rather than from a single model's
first answer — the same instinct behind Mizune's cross-model verification.

`Python` `watsonx` `Granite` `multi-agent`

### 📈 [Multi-Agent Trading Framework](https://github.com/rushikeshgoud19/Trading_bot)

Analyst / research / risk agent teams debating trades, with a TUI, multi-provider LLM support and
India-market coverage. Separating research from risk assessment into different agents means the
agent that wants the trade isn't the one approving it.

`Python` `multi-agent` `LLM routing` `TUI`

### 🚁 RescueWing — autonomous search-and-rescue UAV

450 mm quadcopter (Pixhawk + Raspberry Pi 4) running **YOLOv8-nano** for real-time aerial survivor
detection in flood scenarios. MAVLink waypoint navigation with a lawnmower search pattern, validated
in ArduPilot SITL. Presented at **Makers Conclave 2026**.

### 🎨 Frontend, for the fun of it

[**Mind Universe**](https://github.com/rushikeshgoud19/Mind-Universe-) — cinematic scroll-driven 3D
portfolio with an interactive Earth (Next.js · Three.js) → [minduni.netlify.app](https://minduni.netlify.app)
· [**Black Hole Portfolio**](https://github.com/rushikeshgoud19/blackhole-portfolio.) —
scroll-scrubbed canvas frame animation and a constellation skills map (Next.js · TS)

---

## 📊 Stats

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=rushikeshgoud19&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=rushikeshgoud19&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />

<img height="165" src="https://github-readme-streak-stats.herokuapp.com/?user=rushikeshgoud19&theme=tokyonight&hide_border=true" />

</div>

---

## 🧭 Why I build this way

I like anime, and that's genuinely why Mizune started as a companion rather than a chat box — I
build technical things out of things I actually care about. It turned out to be the best way to learn
distributed systems, because a companion that goes silent at 3 AM is a bug you *feel*.

<div align="center">
<samp>

📫 **rushikeshgoud19@gmail.com** · [Portfolio](https://minduni.netlify.app) · [LinkedIn](https://linkedin.com/in/rushikesh-goud-572007384)

</samp>
</div>
