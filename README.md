<div align="center">

<h1>Kayala Rushikesh Goud</h1>

<h3>AI / LLM Engineer &nbsp;·&nbsp; Autonomous agent systems that verify their own work</h3>

<p>
<samp>CS @ BITS Pilani &nbsp;·&nbsp; Hyderabad, India &nbsp;·&nbsp; open to SDE / AI engineering roles</samp>
</p>

<p>
<a href="https://minduni.netlify.app"><img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio"/></a>
<a href="https://linkedin.com/in/rushikesh-goud-572007384"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
<a href="mailto:rushikeshgoud19@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
<a href="https://github.com/rushikeshgoud19?tab=repositories"><img src="https://img.shields.io/badge/Repositories-181717?style=for-the-badge&logo=github&logoColor=white" alt="Repos"/></a>
</p>

</div>

---

<table>
<tr>
<td width="60%" valign="top">

I build AI agent systems that run on real hardware and do real work — not demos. Mostly **Python,
FastAPI and LLM orchestration**, with a stubborn interest in making agents *verifiable*: systems that
**prove** what they did instead of claiming it.

One conviction runs through everything here: **a model asserting something is not evidence.**

- **Mizune** diffs its own claims against ground-truth seals
- **Project Sovereign** reaches decisions through multi-agent debate
- The **trading framework** keeps the agent that *wants* a trade separate from the one that approves it

Most of what I know came from things breaking in ways I didn't predict.

</td>
<td width="40%" valign="top">

**Currently**

🔨 Building **Mizune** — autonomous assistant, 24/7 on one 898 MB VM
🌱 Contributing to **[traceroot](https://github.com/traceroot-ai/traceroot)** — LLM observability
📚 Studying distributed systems the hard way (production outages)
🎯 Open to **SDE / AI engineer** roles

</td>
</tr>
</table>

---

## 🧰 Tech

<div align="center">

**Languages**

[![Languages](https://skillicons.dev/icons?i=python,typescript,kotlin,cpp,java,js,html,css&theme=dark)](https://skillicons.dev)

**Backend · Infra · Data**

[![Backend](https://skillicons.dev/icons?i=fastapi,nodejs,docker,linux,azure,sqlite,postgres,git,github&theme=dark)](https://skillicons.dev)

**Frontend · Mobile**

[![Frontend](https://skillicons.dev/icons?i=react,nextjs,tailwind,threejs,androidstudio,electron&theme=dark)](https://skillicons.dev)

<samp>

**AI/LLM:** LLM application architecture · tool & function calling · multi-provider routing and failover · RAG ·
vector search & embeddings (ChromaDB) · semantic memory · prompt & context engineering ·
token/cost optimization · LLM evaluation & cross-model verification · multi-agent orchestration
**Vision:** YOLOv8 · MediaPipe · OpenCV &nbsp;|&nbsp; **Robotics:** Pixhawk · MAVLink · ArduPilot · Raspberry Pi

</samp>

</div>

---

## 🚀 Featured Work

### 🤖 [Mizune](https://github.com/rushikeshgoud19/MY-AI) &nbsp;<sub>`Python` `FastAPI` `Azure` `Kotlin` `ChromaDB`</sub>

> **An autonomous AI assistant that runs 24/7 on a single 898 MB VM — and proves what it did.**

<table>
<tr>
<td align="center"><b>Median tokens</b><br/>8.3k → <b>5.2k</b><br/><sub>−37%</sub></td>
<td align="center"><b>Avg latency</b><br/>18.2s → <b>6.3s</b><br/><sub>−65%</sub></td>
<td align="center"><b>Inference cost</b><br/><b>$0</b><br/><sub>7-provider failover</sub></td>
<td align="center"><b>Scale</b><br/><b>~12.6k LOC</b><br/><sub>96 commits · solo</sub></td>
</tr>
</table>

A FastAPI/WebSocket brain on an Azure VM, a WhatsApp interface, an Android client that drives the
phone through a custom `AccessibilityService`, and a three-layer memory system with ChromaDB
semantic recall. Numbers measured across 200 production traces, not estimated.

<details>
<summary><b>The four problems worth reading about</b> ← click</summary>

<br/>

**1. The model lies about its own actions.** It reported *"Task scheduled successfully for 2:32 PM"*
with no row in the scheduler DB — it had pattern-matched an earlier confirmation. Fix: every
side-effecting tool writes a ground-truth seal so claims can be diffed against reality, and anything
that *must* happen gets a deterministic fast-path. **LLMs voice, code delivers.**

**2. My own watchdog was causing the crashes it existed to prevent.** The assistant kept getting
OOM-killed. The app used 220 MB of 898 MB — the rest was **~90 orphaned X11 display servers**,
displays `:120`–`:207`, oldest running 18 days. `xvfb-run -a` allocated a new display per restart and
never cleaned up, and a watchdog restarting every minute meant every crash leaked another one. Swap
sat at 100%. Fixed the process lifecycle; swap dropped to 3%.

**3. Verification is only as good as its evidence.** A mission step failed because the verifier
replied *"I will use the execute_python tool to check…"* — a plan, not evidence. Narration is now
detected deterministically and forces a real check; if it still won't act, the result is an honest
*"inconclusive"* rather than a guess.

**4. Constraints produce better engineering.** 898 MB with `torch` blocked at the import level forced
ONNX embeddings, a hard context-token ceiling, and treating provider *availability* as a first-class
design input. The token work that came out of it cut cost and latency simultaneously.

</details>

---

### 🌱 Open Source — [traceroot-ai/traceroot](https://github.com/traceroot-ai/traceroot)

LLM observability platform. My most useful contribution wasn't a feature — it was noticing the same
`$0`-cost bug had been patched **five separate times**.

| | |
|:--|:--|
| [**#1597**](https://github.com/traceroot-ai/traceroot/issues/1597) | **Root cause** — price resolution implemented twice (Python + TypeScript), no shared contract, no test that the shipped catalog resolves |
| [**#1619**](https://github.com/traceroot-ai/traceroot/pull/1619) | **The fix** — one resolution contract on both sides, most-specific-match ranking, catalog invariant tests → gateway-prefixed model IDs **5/160 → 356/356** |
| [**#1283**](https://github.com/traceroot-ai/traceroot/pull/1283) | Pre-merge row dedup in a ClickHouse `ReplacingMergeTree` query |
| [**#1330**](https://github.com/traceroot-ai/traceroot/pull/1330) | Model-selection persistence in the dashboard UI |

---

### 🏛️ [Project Sovereign](https://github.com/rushikeshgoud19/IBM-Project) &nbsp;<sub>`Python` `watsonx` `Granite`</sub>

An **autonomous AI boardroom** for supply-chain decisions. Specialist agents argue opposing positions
and the decision emerges from the disagreement rather than from one model's first answer.

### 📈 [Multi-Agent Trading Framework](https://github.com/rushikeshgoud19/Trading_bot) &nbsp;<sub>`Python` `multi-agent` `TUI`</sub>

Analyst / research / risk agent teams debating trades, with multi-provider LLM support and
India-market coverage. The agent that wants the trade isn't the one approving it.

### 🚁 RescueWing &nbsp;<sub>`Pixhawk` `YOLOv8` `MAVLink` `ArduPilot`</sub>

450 mm quadcopter (Pixhawk + Raspberry Pi 4) running **YOLOv8-nano** for real-time aerial survivor
detection in flood scenarios. MAVLink waypoint navigation with a lawnmower search pattern, validated
in ArduPilot SITL. **Presented at Makers Conclave 2026.**

### 🎨 Frontend, for the fun of it

[**Mind Universe**](https://github.com/rushikeshgoud19/Mind-Universe-) — cinematic scroll-driven 3D
portfolio with an interactive Earth · Three.js → [minduni.netlify.app](https://minduni.netlify.app)
&nbsp;|&nbsp; [**Black Hole Portfolio**](https://github.com/rushikeshgoud19/blackhole-portfolio.) —
scroll-scrubbed canvas frame animation, constellation skills map

---

## 📊 Stats

<div align="center">

<img height="165" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=rushikeshgoud19&theme=github_dark" alt="stats"/>
<img height="165" src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=rushikeshgoud19&theme=github_dark" alt="most used languages"/>

<img height="165" src="https://github-readme-streak-stats.herokuapp.com/?user=rushikeshgoud19&theme=github-dark&hide_border=true" alt="streak"/>
<img height="165" src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=rushikeshgoud19&theme=github_dark&utcOffset=5.5" alt="productive time"/>

</div>

---

<div align="center">
<samp>

I like anime, and that's genuinely why Mizune started as a companion rather than a chat box —
I build technical things out of things I actually care about.<br/>
It turned out to be the best way to learn distributed systems, because a companion that goes
silent at 3 AM is a bug you <i>feel</i>.

<br/><br/>

📫 **rushikeshgoud19@gmail.com** &nbsp;·&nbsp; [Portfolio](https://minduni.netlify.app) &nbsp;·&nbsp; [LinkedIn](https://linkedin.com/in/rushikesh-goud-572007384)

</samp>
</div>
