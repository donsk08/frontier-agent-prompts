<div align="center">

# 🧠 Frontier Agent Prompts

### The Anatomy of Frontier AI: Production & Reverse-Engineered System Prompts, Behavioral Guidelines, and Hidden Instructions of Claude Code, Cursor, Windsurf, Devin, DeepSeek-R1, and GPT-4o/o3.

[![GitHub Stars](https://img.shields.io/github/stars/donsk08/frontier-agent-prompts?style=for-the-badge&logo=github&color=gold)](https://github.com/donsk08/frontier-agent-prompts/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/donsk08/frontier-agent-prompts?style=for-the-badge&logo=github&color=blue)](https://github.com/donsk08/frontier-agent-prompts/network/members)
[![CI](https://github.com/donsk08/frontier-agent-prompts/actions/workflows/lint.yml/badge.svg)](https://github.com/donsk08/frontier-agent-prompts/actions/workflows/lint.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](CONTRIBUTING.md)
[![Awesome](https://awesome.re/badge.svg)](https://github.com/donsk08/frontier-agent-prompts)

---

> 🌟 **Donsk08 Open Source AI Ecosystem Matrix**:
> - 🛠️ **[awesome-mcp-registry](https://github.com/donsk08/awesome-mcp-registry)**: 1000+ Production MCP Servers & 1-Click Configs
> - 🧠 **[frontier-agent-prompts](https://github.com/donsk08/frontier-agent-prompts)**: Reverse-Engineered System Prompts of Claude, Cursor & Devin
> - 📐 **[universal-agent-rules](https://github.com/donsk08/universal-agent-rules)**: 50+ Production-Hardened .cursorrules & .mdc Templates
> - ⚡ **[free-ai-hub](https://github.com/donsk08/free-ai-hub)**: 100% Free, Zero-Card Required LLM APIs & Free Tiers Directory

---

</div>

## 📖 Table of Contents
- [Executive Overview](#-executive-overview)
- [Prompt Taxonomy & Quick Navigation](#-prompt-taxonomy--quick-navigation)
- [Repository Structure](#-repository-structure)
- [Category Deep Dives](#-category-deep-dives)
  - [1. Anthropic & Claude Ecosystem](#1-anthropic--claude-ecosystem)
  - [2. OpenAI Frontier Models](#2-openai-frontier-models)
  - [3. Autonomous Coding Agents](#3-autonomous-coding-agents)
  - [4. DeepSeek & Open Weights Reasoning](#4-deepseek--open-weights-reasoning)
  - [5. Industrial Agent Architecture Guides](#5-industrial-agent-architecture-guides)
- [How to Use These Prompts](#-how-to-use-these-prompts)
- [Community Star Milestones & Roadmap](#-community-star-milestones--roadmap)
- [Direct 1-Click Raw Access](#-direct-1-click-raw-access-clipboard-ready)
- [Academic Technical Report & Citation](#-academic-technical-report--citation)
- [Contributing](#-contributing)
- [Security Policy](SECURITY.md)
- [Legal, Ethics & Fair-Use Disclaimer](#-legal-ethics--fair-use-disclaimer)
- [License](#-license)

---

## 🔍 Executive Overview

Modern AI development has shifted from simple conversational prompting to **autonomous agent orchestration**. The system prompt is no longer just instructions—it is the **operating kernel** of an agent. It governs:
1. **Tool Invocation Schemas**: Precision execution of bash, file editing, web search, and MCP tools.
2. **Safety & Permission Boundaries**: Defense against remote code execution, prompt injections, and data exfiltration.
3. **Reasoning & State Machines**: Deliberation loops, self-correction, and hypothesis verification before action execution.
4. **Behavioral Grounding**: Eliminating hallucinations and sycophantic flattery in favor of first-principles truth.

**frontier-agent-prompts** is the definitive, curated archive documenting the real-world system prompts, hidden behavioral rules, and architecture blueprints powering the world's most capable AI systems.

### ⭐ Why Star This Repository?

- 🔄 **Continuous Tracking**: Frontier AI providers (Anthropic, OpenAI, Cognition) stealthily update their system instructions monthly. We track diffs, reverse-engineer changes, and catalog new releases within 24 hours.
- 🛡️ **Production-Tested Architectures**: Stop reinventing prompt scaffolding. Copy battle-tested defensive constraints, anti-hallucination guardrails, and tool-invocation contracts directly into your own agents.
- 🚀 **100% Free & Open-Source**: No paywalls, no gating. Everything is transparently documented in standardized Markdown for instant developer productivity.

👉 **Hit the `Star` button in the upper-right corner to bookmark this knowledge base and receive updates on every breakthrough release!**

---

## 🧭 Prompt Taxonomy & Quick Navigation

| Model / System | Category | Key Capabilities & Highlights | Document Link |
| :--- | :--- | :--- | :--- |
| **Claude Code 2.0 CLI** | Anthropic | Full terminal agent loop, tool safety gates, anti-hallucination URL rules | [`claude/claude-code-cli.md`](claude/claude-code-cli.md) |
| **Claude 3.7 Sonnet** | Anthropic | Production system prompt, multi-turn steerability, defensive security bounds | [`claude/claude-3-7-sonnet-system.md`](claude/claude-3-7-sonnet-system.md) |
| **Claude Artifacts** | Anthropic | Rich interactive UI component guidelines, SVG/React/Mermaid specifications | [`claude/claude-artifacts-guidelines.md`](claude/claude-artifacts-guidelines.md) |
| **OpenAI GPT-4o** | OpenAI | Full vision-enabled personality spec, image group schemas, multi-modal formatting | [`openai/gpt-4o-system.md`](openai/gpt-4o-system.md) |
| **OpenAI o1 Reasoning** | OpenAI | Deliberation channel architecture, test-time compute, mathematical decomposition | [`openai/o1-reasoning-system.md`](openai/o1-reasoning-system.md) |
| **OpenAI o3-High API** | OpenAI | High-reasoning verbosity protocols, Yap score calibration, channel validation | [`openai/o3-reasoning-system.md`](openai/o3-reasoning-system.md) |
| **OpenAI Codex Plan Mode** | OpenAI | Spec-first architecture decomposition, plan generation, and task breakdown | [`openai/openai-codex-plan-mode.md`](openai/openai-codex-plan-mode.md) |
| **OpenAI Deep Research** | OpenAI | Multi-step web synthesis, iterative citation trees, exploratory search logic | [`openai/openai-deep-research.md`](openai/openai-deep-research.md) |
| **Cursor Agent v2.0** | Coding Agent | Full workspace context injection, diff generation contracts, semantic grep | [`coding-agents/cursor-agent-v2.md`](coding-agents/cursor-agent-v2.md) |
| **Cursor CLI Agent** | Coding Agent | Terminal-first execution rules, headless patch application, linter recovery | [`coding-agents/cursor-cli-prompt.md`](coding-agents/cursor-cli-prompt.md) |
| **Windsurf Cascade** | Coding Agent | Codebase-wide multi-file orchestration, wave execution protocol, real-time sync | [`coding-agents/windsurf-cascade-prompt.md`](coding-agents/windsurf-cascade-prompt.md) |
| **Aider Dual-Model** | Coding Agent | Decoupled Architect/Editor pipeline, Repo-Map AST injection, search/replace diffs | [`coding-agents/aider-architect-editor.md`](coding-agents/aider-architect-editor.md) |
| **Devin AI** | Coding Agent | End-to-end autonomous software engineer runtime, shell execution loop | [`coding-agents/devin-ai-prompt.md`](coding-agents/devin-ai-prompt.md) |
| **Cline (Claude Dev)** | Coding Agent | Autonomous VS Code extension prompt, browser automation, read-write tools | [`coding-agents/cline-dev-system.md`](coding-agents/cline-dev-system.md) |
| **Roo-Code** | Coding Agent | Multi-mode autonomous developer prompt (Architect / Code / Ask) | [`coding-agents/roo-code-system.md`](coding-agents/roo-code-system.md) |
| **Manus Agent Loop** | Coding Agent | General-purpose autonomous browser and shell execution state machine | [`coding-agents/manus-agent-loop-prompt.md`](coding-agents/manus-agent-loop-prompt.md) |
| **Manus Agent Modules** | Coding Agent | Modular capability definitions, tool execution contracts, and sandbox APIs | [`coding-agents/manus-agent-modules.md`](coding-agents/manus-agent-modules.md) |
| **DeepSeek-R1** | Open Weights | Large-scale RL reasoning framework, `<think>` boundary isolation, proof engine | [`deepseek-open-source/deepseek-r1-system.md`](deepseek-open-source/deepseek-r1-system.md) |
| **DeepSeek-V3** | Open Weights | Mixture-of-Experts architecture prompt, high-throughput code synthesis | [`deepseek-open-source/deepseek-v3-system.md`](deepseek-open-source/deepseek-v3-system.md) |
| **Industrial Prompt Architecture** | Whitepaper | 7-layer compiled execution kernel blueprint, anti-injection gates | [`architecture-guides/industrial-agent-prompt-architecture.md`](architecture-guides/industrial-agent-prompt-architecture.md) |
| **Tool Use & Agentic Loop** | Whitepaper | State machine design, idempotent error recovery, JSON stream enforcers | [`architecture-guides/tool-use-and-agentic-loop-patterns.md`](architecture-guides/tool-use-and-agentic-loop-patterns.md) |

---

## 📂 Repository Structure

```text
frontier-agent-prompts/
├── .github/
│   └── workflows/
│       └── lint.yml                             # Automated Markdown & link CI
├── architecture-guides/
│   ├── industrial-agent-prompt-architecture.md  # 7-layer compiled kernel design guide
│   └── tool-use-and-agentic-loop-patterns.md   # Production agent loop state machine
├── claude/
│   ├── claude-3-7-sonnet-system.md              # Claude 3.7 production system prompt
│   ├── claude-artifacts-guidelines.md           # Interactive Artifacts UI engine rules
│   └── claude-code-cli.md                       # Claude Code 2.0 autonomous CLI agent
├── coding-agents/
│   ├── aider-architect-editor.md                # Aider decoupled Architect / Editor engine
│   ├── cline-dev-system.md                      # Cline (Claude Dev) autonomous engine
│   ├── cursor-agent-v2.md                       # Cursor Composer v2 core instructions
│   ├── cursor-cli-prompt.md                     # Cursor CLI terminal agent
│   ├── devin-ai-prompt.md                       # Devin AI autonomous software engineer
│   ├── manus-agent-loop-prompt.md               # Manus autonomous execution loop
│   ├── manus-agent-modules.md                   # Manus modular capability definitions
│   ├── roo-code-system.md                       # Roo-Code multi-role agent prompts
│   └── windsurf-cascade-prompt.md               # Windsurf Cascade Wave 11 instructions
├── deepseek-open-source/
│   ├── deepseek-r1-system.md                    # DeepSeek-R1 reasoning & <think> protocol
│   └── deepseek-v3-system.md                    # DeepSeek-V3 MoE production system prompt
├── openai/
│   ├── gpt-4o-system.md                         # GPT-4o production system prompt & UI spec
│   ├── o1-reasoning-system.md                   # o1 series deliberation & verification rules
│   ├── o3-reasoning-system.md                   # o3 series high-compute reasoning API prompt
│   ├── openai-codex-plan-mode.md                # Codex Plan Mode architectural decomposition
│   └── openai-deep-research.md                  # Deep Research multi-step search engine
├── publications/
│   ├── frontier_agent_prompts_technical_report.html # Monograph HTML source
│   └── frontier_agent_prompts_technical_report.pdf  # Camera-ready technical report PDF
├── CONTRIBUTING.md                              # Open source contribution guide
├── LICENSE                                      # MIT License
├── SECURITY.md                                  # Responsible disclosure & privacy policy
└── README.md                                    # Master documentation & navigation hub
```

---

## 🔬 Category Deep Dives

### 1. Anthropic & Claude Ecosystem
Anthropic's system prompt design philosophy emphasizes **Constitutional AI, defensive security constraints, and precision artifact generation**.
- **Claude Code 2.0 CLI** demonstrates how to build a production command-line agent: preventing unauthorized file creation, enforcing existing file edits over new file proliferation, and strictly sandboxing network calls.
- **Claude Artifacts** provides the definitive specification for rendering self-contained SVG, React components, and HTML snippets in a sandboxed iframe.

### 2. OpenAI Frontier Models
OpenAI's latest generation prompts highlight the transition to **multi-channel reasoning and tool integration**:
- **GPT-4o** contains elaborate specifications for structured visual output (`image_group`), entity references, and anti-sycophancy guidelines.
- **o1 & o3 series** show how test-time compute is governed, separating internal chain-of-thought tokens from user-facing deliverables and enforcing deterministic complexity bounds.

### 3. Autonomous Coding Agents
The heart of modern agentic engineering:
- **Cursor Composer & CLI**: Optimized for diff generation, workspace-wide symbol awareness, and minimal token overhead.
- **Windsurf Cascade**: Pioneered the concept of "Wave execution"—coordinated multi-file updates synchronized with LSP feedback.
- **Cline & Roo-Code**: Open-source implementations demonstrating how to give LLMs full terminal, browser, and file system execution with human-in-the-loop safety switches.
- **Aider**: Pioneered the dual-model Architect / Editor decoupled pipeline with tree-sitter AST Repo-Map injection and surgical search/replace unified diffs.
- **Devin & Manus**: High-autonomy agent architectures that manage persistent shell environments, browser CDP sessions, and dynamic planning boards.

### 4. DeepSeek & Open Weights Reasoning
DeepSeek-R1 is a landmark achievement in open-source AI:
- Unconstrained `<think> ... </think>` test-time exploration enables the model to self-correct, generate edge cases, and prove algorithmic correctness.
- Our templates demonstrate how to extract maximum reasoning performance from open-weights models in local vLLM or Ollama environments.

### 5. Industrial Agent Architecture Guides
Authored for software architects and senior prompt engineers:
- **7-Layer Compiled Kernel Model**: How to structure prompts for zero prompt injection vulnerability and 100% deterministic JSON output.
- **State Machine Loop Protocols**: How to build watchdogs, error recovery circuits, and anti-infinite-loop tripwires into autonomous agents.

---

## 🚀 How to Use These Prompts

### Integrating into Custom Agents
To use any of these system instructions in your own LangChain, LlamaIndex, AutoGen, or custom agent loop:
1. Navigate to the relevant markdown file (e.g., [`claude/claude-code-cli.md`](claude/claude-code-cli.md)).
2. Copy the system prompt block into your agent's initial `SystemMessage` or developer instructions.
3. Replace template placeholders (e.g., `{{USER_PROBLEM}}`, `{{WORKSPACE_DIRECTORY}}`) with your runtime environment parameters.

### Local Testing with Ollama or vLLM
```bash
# Example: Running DeepSeek-R1 reasoning template with Ollama
ollama run deepseek-r1:32b "$(cat deepseek-open-source/deepseek-r1-system.md)"
```

---

## 🌟 Community Star Milestones & Roadmap

We unlock new reverse-engineered architectures and open-source tooling at each community milestone:

- [x] ⭐️ **1 Star (Genesis)**: Official release cataloging Claude Code, Claude 3.7, GPT-4o, Cursor, Devin & DeepSeek-R1.
- [ ] ⭐️ **100 Stars**: Add **DeepSeek-V3** full multi-tool calling specification & function calling benchmarks.
- [ ] ⭐️ **250 Stars**: Add **Grok-3 / Grok-2** system prompts and reasoning trace decompilations.
- [ ] ⭐️ **500 Stars**: Launch **1-Click CLI Utility** (`npx frontier-prompts add <agent>`) to inject prompts directly into projects.
- [ ] ⭐️ **1,000 Stars**: Release the **Automated Agent Prompt Injection & Jailbreak Defense Benchmark**.

---

## ⚡ Direct 1-Click Raw Access (Clipboard Ready)

Need a prompt immediately in your terminal or editor? Pipe raw prompts directly to your clipboard or project:

```bash
# Claude Code 2.0 CLI Production Prompt
curl -fsSL https://raw.githubusercontent.com/donsk08/frontier-agent-prompts/main/claude/claude-code-cli.md

# Cursor Composer v2.0 System Prompt
curl -fsSL https://raw.githubusercontent.com/donsk08/frontier-agent-prompts/main/coding-agents/cursor-agent-v2.md

# DeepSeek-R1 Reasoning & Chain-of-Thought Guardrails
curl -fsSL https://raw.githubusercontent.com/donsk08/frontier-agent-prompts/main/deepseek-open-source/deepseek-r1-system.md
```

---

## ⭐ Star History

<div align="center">

[![Star History Chart](https://api.star-history.com/svg?repos=donsk08/frontier-agent-prompts&type=Date)](https://star-history.com/#donsk08/frontier-agent-prompts&Date)

</div>

---

## 📄 Academic Technical Report & Citation

This repository accompanies our formal research monograph on the architecture, safety, and evaluation of autonomous coding agent prompts:

- 📑 **Read Online HTML**: [`publications/frontier_agent_prompts_technical_report.html`](publications/frontier_agent_prompts_technical_report.html)
- 📥 **Download Camera-Ready PDF**: [`publications/frontier_agent_prompts_technical_report.pdf`](publications/frontier_agent_prompts_technical_report.pdf)

### BibTeX Citation
If you use these prompts, architecture guides, or benchmarks in your research or commercial products, please cite:

```bibtex
@article{donsk2026frontierprompts,
  title={Frontier Agent Prompts: The 7-Layer Compiled Kernel Model and State Machine Loop Protocols for Autonomous Coding Systems},
  author={DONSK},
  journal={Frontier AI Systems Lab Technical Report},
  year={2026},
  month={October},
  note={ORCID: 0009-0004-2951-0263},
  url={https://github.com/donsk08/frontier-agent-prompts}
}
```

---

## 🤝 Contributing

We welcome contributions from AI researchers, prompt engineers, and open-source developers worldwide!
Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for details on:
- How to submit new system prompts or updates
- Formatting standards and redaction requirements (strictly no personal tokens or credentials)
- Pull request review process

---

## ⚖️ Legal, Ethics & Fair-Use Disclaimer

### 1. Academic Research & Fair Use Doctrine (17 U.S.C. § 107)
The system prompts, reverse-engineered architectures, and behavioral protocols cataloged in this repository are published strictly for **scholarly research, educational analysis, interoperability assessment, and defensive AI safety auditing** under the principles of **Fair Use** (Title 17, United States Code, Section 107), the European Union Information Society Directive (2001/29/EC Art. 5(3)(a)), and equivalent international statutory research exceptions.
- **Transformative Scholarship**: This repository does not redistribute proprietary model binaries or API access. Rather, it synthesizes raw prompt phenomena into novel academic formalisms (e.g., our formal *7-Layer Compiled Kernel Model* and *Idempotent State Machine Protocols*), providing empirical failure-mode taxonomy, sycophancy mitigation metrics, and defensive engineering baselines.
- **Non-Copyrightability of Utilitarian Functional Matter**: In accordance with 17 U.S.C. § 102(b), the Merger Doctrine (*Baker v. Selden*), and *Google LLC v. Oracle America, Inc.* (2021), functional interface specifications, tool execution schemas, and operational instructions governing machine behavior represent functional methods of operation rather than protectable expressive works.

### 2. Nominative Fair Use & Trademark Attribution
All product names, logos, brands, service marks, and registered trademarks cited in this repository (including but not limited to **Anthropic, Claude, OpenAI, ChatGPT, GPT-4o, Cursor, Anysphere, Windsurf, Codeium, Devin, Cognition AI, DeepSeek**) are the intellectual property of their respective owners.
- Their citation within this repository is strictly for **identification and nominative commentary** under the Nominative Fair Use doctrine (*New Kids on the Block v. News America Publishing, Inc.*, 9th Cir. 1992).
- This repository is an independent open-source research initiative. It is **not affiliated with, endorsed by, sponsored by, or in any way officially associated with** Anthropic, OpenAI, Cursor / Anysphere, Codeium, Cognition AI, DeepSeek, or any of their affiliates or subsidiaries.

### 3. Terms of Service & Benign Research Boundaries
All prompt telemetry and behavioral data documented herein have been compiled from publicly accessible documentation, benign user interactions, and standard client telemetry for legitimate safety interpretability research. We do not distribute private access keys, bypass paywalled authentication gates, or access protected computer systems without authorization (*Van Buren v. United States*, 2021; DMCA § 1201 Good-Faith Security Research Exemptions).

### 4. Notice and Takedown Policy (DMCA Safe Harbor Protocol)
We respect intellectual property rights and maintain a cooperative, good-faith relationship with AI researchers and developers worldwide. If you are a copyright or trademark owner (or an authorized agent) and believe that any content in this repository exceeds fair-use research boundaries or contains proprietary trade secrets:
- Please submit a notice via [GitHub Private Vulnerability Reporting](https://github.com/donsk08/frontier-agent-prompts/security/advisories) or contact maintainer [@donsk08](https://github.com/donsk08).
- We maintain a **24–48 hour remediation SLA** and will expeditiously review, redact, contextualize, or remove contested material in good faith.

---

## 📜 License

- **Source Code, Architecture Guides & Original Technical Reports**: Distributed under the permissive [MIT License](LICENSE). &copy; 2026 DONSK.
- **Third-Party Prompts & Reference Instructions**: Documented strictly under Fair Use for scholarship, safety evaluation, and comparative benchmarking.

---

<div align="center">

**Star ⭐ this repository to stay ahead of the AI Agent frontier!**

</div>
