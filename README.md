# Awesome Claude Code from China [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 在中国大陆跑通、并**验证**Claude Code(及 Cursor/Cline/Codex)的一切:接入方式、
> 配置工具、验降智、自建网关、客户端、省钱、避坑。
> A curated list for running Claude Code from mainland China — access, setup,
> verification, self-hosting, clients, cost, and troubleshooting.

用 Claude Code 在国内卡三件事:**付不了**(没海外卡)、**怕封号**、**怕降智**(中转偷偷换小
模型)。这份清单把每一环的资源、工具、坑收在一处。**核心原则:别信任何中转的口头承诺,
自己验。**

> **Disclosure:** maintained by the team behind [cocodot](https://cocodot.co), a relay.
> cocodot and its tools appear as *disclosed* entries; neutral/competing tools are
> listed on equal terms. Everything here works vendor-neutrally — verify yourself.

## Contents
- [Access paths](#access-paths)
- [Setup & config](#setup--config)
- [Verify no downgrade](#verify-no-downgrade)
- [Cost](#cost)
- [Self-hosted gateways](#self-hosted-gateways)
- [Editors & clients](#editors--clients)
- [Guides & reading](#guides--reading)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## Access paths
How to get Claude Code talking to a model from China. Full comparison:
[claude-code-china-direct](https://github.com/cocodot2026/claude-code-china-direct).
- **Official** — Anthropic direct; needs an overseas card + stable network; no downgrade risk.
- **API relay / 中转** — point `ANTHROPIC_BASE_URL` at a compatible endpoint; often Alipay/CNY, usually no 梯子; **downgrade risk → verify**.
- **Self-host** — run your own gateway with your own upstream keys (see below).

## Setup & config
- [ccsetup](https://github.com/cocodot2026/ccsetup) — one command to configure Claude Code for any relay + smoke-test it (zero deps).
- [relay-doctor](https://github.com/cocodot2026/relay-doctor) — one command to health-check any relay (reachable? models? latency? streaming?).
- [ai-coding-from-china](https://github.com/cocodot2026/ai-coding-from-china) — a Claude Code skill: pick a path → configure → verify → cut cost → fix errors.
- Claude Code env vars: `ANTHROPIC_BASE_URL`, `ANTHROPIC_AUTH_TOKEN`, `ANTHROPIC_MODEL`, `ANTHROPIC_SMALL_FAST_MODEL`.

## Verify no downgrade
The step everyone skips. **Behavior fingerprints, not "what model are you?".** Use more
than one independent tool — a score you can only get from one vendor isn't verification.
- [ai-relay-verified](https://github.com/cocodot2026/ai-relay-verified) — a directory that *scores* relays on verifiability, with a reproducible method.
- [cocodot-llmprobe](https://github.com/cocodot2026/cocodot-llmprobe) — 6-probe 0–100 verifier, key stays local.
- [LLMprobe-engine](https://github.com/Bazaarlinkorg/LLMprobe-engine) — independent; 36 probes / 8 dimensions; ran a 171-endpoint study.
- [llm-probe](https://github.com/telagod/llm-probe) — independent; protocol + injection-resistance + trust score.

## Cost
- [ai-api-cost](https://github.com/cocodot2026/ai-api-cost) — honest token-cost estimator; real token counts × rates you supply, no guessed prices.
- [model-id-cheatsheet](https://github.com/cocodot2026/model-id-cheatsheet) — which relay model id maps to which real model.
- Tip: split `ANTHROPIC_MODEL` (flagship) vs `ANTHROPIC_SMALL_FAST_MODEL` (small) — most token volume runs cheap.

## Self-hosted gateways
Run your own, plug in your own upstream keys — full control, code never transits a third party.
- [one-api](https://github.com/songquanpeng/one-api) — mature Go/Vue aggregation gateway.
- [new-api](https://github.com/QuantumNous/new-api) — multi-tenant fork with billing & admin UI.
- [LiteLLM](https://github.com/BerriAI/litellm) — 100+ providers behind one OpenAI-compatible proxy.

## Editors & clients
- **Claude Code** — Anthropic's CLI; reads `ANTHROPIC_*`.
- **Cursor** — set an OpenAI-compatible base URL + key in Models settings.
- **Cline** (VS Code) — "OpenAI Compatible" provider.
- **Cherry Studio / Chatbox / LobeChat** — GUI clients; set API host to your endpoint.
- **Codex CLI** — reads `OPENAI_BASE_URL` / `OPENAI_API_KEY`.

## Guides & reading
- [claude-code-china-direct](https://github.com/cocodot2026/claude-code-china-direct) — official vs relay vs self-host, and how to verify.
- [llm-relay-degradation-check](https://github.com/cocodot2026/llm-relay-degradation-check) — the 3 downgrade tricks + how to catch them.
- [subscribe-ai-from-china](https://github.com/cocodot2026/subscribe-ai-from-china) — subscribing to overseas AI from China.
- [Anthropic API top-up from China (Alipay)](https://cocodot.co/hub/anthropic-api) — maintainer's own guide (cocodot), disclosed.
- [2026 China AI API relay comparison](https://cocodot.co/hub/shenma-teamorouter-api2d-compare) — side-by-side relay landscape; maintainer builds one of them, disclosed, competitors on equal terms.

## Troubleshooting
- `401/403` — wrong key, or wrong endpoint (Claude Code wants the **Anthropic**-compatible URL; Cursor/Cline want the **OpenAI** one, usually `/v1`).
- `model not found` — the model id is relay-specific; use the id your relay exposes.
- timeouts / streaming fails — relay streaming may be flaky; try non-streaming; re-verify at peak hours.
- Cursor account banned — bans target the account/environment, not you; an API key in Cline/Claude Code has no login to ban.

## Contributing
PRs welcome — add a tool, guide, or tip. **One item per PR, real & useful, disclose
affiliation, no affiliate links, competitors welcome on equal terms.** See [CONTRIBUTING.md](CONTRIBUTING.md).

## License
[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/) — CC0. Copy and reuse freely.
