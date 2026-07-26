# Hey, I'm Rushikesh 👋

I build AI agent systems that run on real hardware and do real work — not demos. Mostly Python,
FastAPI, and LLM orchestration, with a stubborn interest in making agents *verifiable*: systems
that prove what they did instead of claiming it.

CS @ BITS Pilani · Hyderabad, India · open to SDE / AI engineering roles

---

## Featured Work

### 🤖 [Mizune](https://github.com/rushikeshgoud19/MY-AI) — autonomous AI assistant, 24/7 on one 898MB VM

A self-hosted assistant with a FastAPI/WebSocket brain on an Azure VM, a WhatsApp interface, an
Android client that controls the phone through a custom `AccessibilityService`, and a three-layer
memory system with ChromaDB semantic recall. Solo, ~96 commits.

The interesting part wasn't building it — it was keeping it alive:

- **Runs on $0 of inference spend** — a 7-provider failover cascade with per-key rotation, so when
  one provider hits its daily token cap mid-request, the next picks up.
- **Cut median input tokens 37%** (8.3k → 5.2k) and **average latency 65%** (18.2s → 6.3s), measured
  across 200 production traces rather than estimated.
- **It verifies its own claims.** LLMs will confidently report doing things they didn't — mine
  reported scheduling a task that was never scheduled. Now every action writes a ground-truth
  record, and multi-step tasks must prove each step against real system state before advancing.
- **Evaluation harness** scoring each provider on response fidelity and tool-selection correctness,
  plus cross-model verification (a different model checks the answer than produced it).
- When it kept crashing, I traced it to ~90 orphaned X11 display servers leaked one per restart over
  18 days. My own watchdog was causing the crashes it existed to prevent.

`Python` `FastAPI` `WebSocket` `Azure` `Kotlin/Android` `ChromaDB` `Linux`

### 🌱 Open source — [traceroot-ai/traceroot](https://github.com/traceroot-ai/traceroot)

Contributing to an LLM observability platform. Most recent:
[**#1597**](https://github.com/traceroot-ai/traceroot/issues/1597) — root-caused why the same
`$0`-cost bug had been patched five separate times (price resolution implemented twice, Python and
TypeScript, with no shared contract or catalog invariants), and
[**#1619**](https://github.com/traceroot-ai/traceroot/pull/1619) fixes the class rather than the
symptom: one resolution contract on both sides, most-specific-wins matching, and catalog invariant
tests so the next model launch can't silently break pricing.

Earlier: detector-run deduplication ([#1283](https://github.com/traceroot-ai/traceroot/pull/1283)),
model-selection persistence ([#1330](https://github.com/traceroot-ai/traceroot/pull/1330)).

### 🚁 RescueWing — autonomous search-and-rescue UAV

450mm quadcopter (Pixhawk + Raspberry Pi 4) running YOLOv8-nano for real-time aerial survivor
detection in flood scenarios. MAVLink waypoint navigation with a lawnmower search pattern, validated
in ArduPilot SITL. Presented at **Makers Conclave 2026**.

### 🧠 [Mind Universe](https://github.com/rushikeshgoud19/Mind-Universe-)

Full-stack Next.js platform with agent-based AI features, CI on Netlify.
Live at [minduni.netlify.app](https://minduni.netlify.app)

---

## Stack

**Languages** Python · TypeScript · Kotlin · C++ · SQL
**AI/LLM** LLM application architecture · tool/function calling · RAG · vector search (ChromaDB) ·
multi-provider routing & failover · prompt & context engineering · LLM evaluation · multi-agent orchestration
**Backend** FastAPI · WebSocket · REST · SQLite · Docker · Linux · Azure · distributed tracing
**Frontend/Mobile** React · Next.js · Tailwind · Android (Kotlin)
**Vision** YOLOv8 · MediaPipe · OpenCV

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=rushikeshgoud19&layout=compact&theme=tokyonight&hide_border=true)

---

## Why I build this way

I like anime, and that's genuinely why Mizune started as a companion rather than a chat box — I
build technical things out of things I actually care about. It turned out to be the best way to
learn distributed systems, because a companion that goes silent at 3am is a bug you *feel*.

📫 rushikeshgoud19@gmail.com · [Portfolio](https://minduni.netlify.app) · [LinkedIn](https://linkedin.com/in/rushikesh-goud)
