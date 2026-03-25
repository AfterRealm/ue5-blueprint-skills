# UE5 Blueprint Skills for Claude Code

**The first AI plugin that actually reads your Blueprints.**

---

Stop describing your node graph in chat. Stop screenshotting spaghetti and hoping the AI can parse it. UE5 Blueprint Skills connects Claude Code directly to your running Unreal Editor — it exports the actual Blueprint data, reads every node and wire, and tells you exactly what's wrong and how to fix it.

## What makes this different

Every other AI coding tool treats Blueprints like a black box. You describe what you built, the AI guesses at what you meant, and you go back and forth until someone gives up.

This plugin gives Claude **eyes**.

It connects to your UE5 Editor through Python remote execution, exports your Blueprint graphs as structured data, and runs them through 25 known anti-patterns and 15+ heuristic health checks. When it finds a problem, it doesn't give you a vague "check your connections" — it tells you exactly which node, which pin (by color and side), and what wire to drag where.

## The Pipeline

```
Your UE5 Editor  →  Python Remote Export  →  T3D / JSON  →  Wiring Maps  →  Analysis
```

One command to export. One command to audit. One command to fix. No clipboard gymnastics.

## What it catches

**The bugs that cost you hours:**
- BreakStruct copy bugs — you're writing to a photocopy, not the original. The data looks right in the editor but nothing actually changes at runtime.
- Delay inside ForEachLoop — the loop doesn't wait. Only the last iteration fires.
- GetAllActorsOfClass on Tick — congrats, you're iterating every actor in your level 60 times a second.
- Widget leaks — Create Widget without checking if one already exists. Memory climbs until the game crashes.

**25 patterns total**, from critical data-loss bugs to subtle performance killers. Plus heuristic checks for dead-end execution paths, orphaned nodes, missing null checks, and cross-function consistency.

## Built for visual learners

Every fix instruction follows a strict teaching system designed for people who think in nodes, not code:

> *"Drag a wire from the **dark teal output pin** on the **right side** of **Array Length** to the **cyan input pin** on the **left side** of the **> (Greater Than)** node."*

Pin colors. Pin sides. Exact search terms. One step at a time. No jargon without definition. No forward references. No "connect the output to the input" without saying WHICH output and WHICH input.

You don't need to be a programmer. You need to be able to right-click and search.

## 1,864 node cards

Every node in the UE5 Blueprint API, scraped from Epic's official docs. Organized into 52 categories. When Claude suggests a node, it knows the inputs, outputs, pin types, and what it actually does — not a hallucinated guess.

## Setup in 2 minutes

1. Enable the Python plugin in your UE5 Editor (Edit > Plugins)
2. Turn on Remote Execution (Edit > Project Settings > Python)
3. `pip install upyrc`
4. Load the plugin: `claude --plugin-dir ue5-blueprint-skills`
5. `/ue5-blueprints:setup` to verify the connection

That's it. Your UE5 Editor is now connected to Claude.

## Who this is for

- **Solo devs** who don't have a second pair of eyes on their Blueprints
- **Modders** building on games with complex Blueprint frameworks
- **Teams** where the Blueprint person isn't the programming person
- **Anyone** who's ever stared at a Blueprint bug for 3 hours and it turned out to be one missing wire

---

*Built by someone who's been there. Every pattern in this plugin was discovered the hard way.*

---

**MIT Licensed** | **Claude Code Plugin** | **UE5 5.0+**
