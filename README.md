### Hey, I'm Nitin

[X @NitinKu71959413](https://x.com/NitinKu71959413) · [blog](https://medium.com/@Nitin_Indian) · [email](mailto:internshipsvc01@gmail.com)

![tests passing](https://img.shields.io/badge/tests-42%20passing-brightgreen) ![focus](https://img.shields.io/badge/focus-agent%20security%20harnesses-red)

I work on AI harness engineering — building the scaffolding agents run, eval, and get benchmarked in. I contribute to [REA](https://github.com/morluto/rea) (reverse engineer anything with agents, from app behavior down to native binaries) and [vLLM](https://github.com/vllm-project/vllm).

Lately I've been benchmarking agents against xbow/xben-style security challenges using [PentAGI](https://github.com/vxcontrol/pentagi) and [HackerAgent](https://github.com/pushpenderindia/hackeragent).

#### Building — the harness stack
- [**EvoBench**](https://github.com/Nitin13-git/evobench) ![flagship](https://img.shields.io/badge/flagship-orange) — A benchmark suite that grows itself. Mines real failures caught by VerifyLoop into permanent regression tasks, stores them tamper-evidently in ReceiptLedger, and runs them through HarnessBench — so every model gets benchmarked against every failure the harness has actually hit, with no one hand-writing the task.
- [**HCP**](https://github.com/Nitin13-git/hcp) — Harness Context Protocol. Standardizes the four subsystems an agent harness needs: durable state outside the context window, independent verification evidence instead of self-reported success, least-privilege scope, and init/checkpoint/teardown session lifecycle. Ships a reference SDK plus a conformance validator that checks any harness implementation against the spec.
- [**AgentCage**](https://github.com/Nitin13-git/agentcage) ![security-critical](https://img.shields.io/badge/security--critical-red) — Least-privilege sandboxing for a single agent session. Patches `open`, `subprocess.Popen`, and `socket.connect` directly, so a declared scope is enforced at the three points almost everything in the standard library funnels through, not left as an advisory convention the agent's own code has to remember to check.
- [**HarnessBench**](https://github.com/Nitin13-git/harnessbench) — Benchmarks agent harnesses across models on tasks that grade independently, never self-report. One OpenAI-compatible adapter reaches open-weight and closed models alike — MiniMax-M2.5, GLM-5, Kimi-K2.5, Devstral-2-123B, Qwen3-235B, GPT-OSS-120B, DeepSeek-V3.2, Claude Sonnet 4.5 — through a single interface, and reports success rate, latency, cost, and context-token usage as one comparison table.
- [**VerifyLoop**](https://github.com/Nitin13-git/verifyloop) — Runs a verification command, parses real pass/fail/error counts rather than trusting output, and categorizes failures by exception type straight from the traceback. Keeps an append-only progress log so a session that gets interrupted and resumed can check what already passed instead of re-running everything.
- [**ReceiptLedger**](https://github.com/Nitin13-git/receiptledger) — Append-only, hash-chained receipt log for agent sessions. A side index maps each key to the byte offset of its latest receipt for O(1) head lookup regardless of ledger size, and optimistic-concurrency conflict detection catches two sessions writing the same key without having seen each other's latest write.
- [**learn-harness-security**](https://github.com/Nitin13-git/learn-harness-security) ![capstone](https://img.shields.io/badge/capstone-brightgreen) — A course on harness engineering for the adversarial case specifically: running an agent against security-benchmark tasks where the target is actively trying to escape scope and fake its own verification. Lectures plus a hands-on project wiring the tools above around a toy exploit target, verified through an independent side channel instead of the agent's own report.

#### Contributing to
- [**REA**](https://github.com/morluto/rea) — Reverse engineer anything with agents, from app behavior down to native binaries.
- [**vLLM**](https://github.com/vllm-project/vllm) — High-throughput LLM inference and serving engine.

#### Benchmarking
Running agents through xbow/xben-style offensive-security benchmarks with:
- [PentAGI](https://github.com/vxcontrol/pentagi)
- [HackerAgent](https://github.com/pushpenderindia/hackeragent)
