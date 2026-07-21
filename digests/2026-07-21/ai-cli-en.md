# AI CLI Tools Community Digest 2026-07-21

> Generated: 2026-07-21 14:17 UTC | Tools covered: 4

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## Cross-Tool Comparison

# AI CLI Tools Ecosystem Cross-Tool Comparison Report
**Date:** 2026-07-21

---

## 1. Ecosystem Overview

The AI CLI tools landscape is experiencing a phase of rapid maturation, with all four major tools (Claude Code, OpenAI Codex, Gemini CLI, GitHub Copilot CLI) shipping releases this week and addressing community feedback at scale. The dominant theme across ecosystems is **infrastructure reliability** — teams are prioritizing bug fixes for session persistence, billing accuracy, and cross-platform parity over flashy new features. However, significant **rollout friction** around model access (Fable 5, GPT-5.6-sol, BYOK configurations) and **silent failure modes** (false success reports, hanging agents, invisible errors) remain the top sources of community frustration across all tools. The plugin/hooks ecosystem is expanding rapidly, but onboarding friction and documentation gaps are creating barriers to adoption that developers are voicing loudly.

---

## 2. Activity Comparison

| Metric | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI |
|---|---|---|---|---|
| **Issues (hot/filed)** | 10 hot issues; 3+ new high-severity billing bugs | 10 hot issues; 2 new data-usage/security issues filed | 10 hot issues; active triage across subagent/permission bugs | 12 new triage items today; 10 noteworthy open issues |
| **PRs (active today)** | 10 key PRs merged; plugin/hooks ecosystem fixes dominate | 15+ infrastructure PRs landed; proxy, sandbox, MCP improvements | 10+ PRs; heavy A2A security + SSR pipeline work | 0 PRs updated in 24h (quieter day) |
| **Release status** | **v2.1.216** — critical quadratic slowdown fix + new setting | **4 alpha releases** (v0.145.0-alpha.25–29); rapid iteration | **v0.52.0-nightly** — automated nightly, no user-facing changes | **v1.0.72 + v1.0.73** — agentStop fix + subagent improvements |
| **Release velocity** | Weekly stable releases | Daily alpha churn | Nightly automated builds | Weekly/bi-weekly patches |

**Key observation:** OpenAI Codex is iterating fastest (4 alphas/day) but with no changelogs, suggesting internal stabilization work. Gemini CLI shows strong infrastructure investment (security + automation). Copilot CLI had a PR pause but shipped two patches. Claude Code continues weekly stable releases with significant bug fixes.

---

## 3. Shared Feature Directions

The following requirements appear across **multiple tool communities**, indicating market-wide developer needs:

| Requirement | Tools Affected | Specific Needs |
|---|---|---|
| **Multi-account / profile switching** | Claude Code (#18435, 669👍), Copilot CLI (implied in enterprise billing requests) | Work/personal account separation, seamless desktop switching |
| **Per-agent/default model configuration** | Copilot CLI (#2193, #4190), Gemini CLI (#21968), Claude Code (#79337) | Global defaults for subagents, quick model cycling in TUI |
| **Agent/Workflow observability** | Claude Code (#69094, #76727), Copilot CLI (#4207), Gemini CLI (#22598) | SDK-level subagent queues, per-agent credit breakdowns, trajectory visibility |
| **Cross-platform parity (Linux/Windows)** | Claude Code (#62699 — Linux copy), Codex (#11023 — Linux desktop, #23198 — Windows perf), Copilot CLI (#3622 — Windows clipboard) | Linux desktop apps, Windows clipboard/performance, consistent keyboard handling |
| **Configurable timeouts / auto-resolve** | Codex (#28969, 147👍), Gemini CLI (#25166), Copilot CLI (implicit in agentStop hooks) | Disable 60-second auto-resolve, prevent agent hangs, graceful termination |
| **BYOK / custom model integration** | Copilot CLI (#4012, #4196), Claude Code (Fable 5 billing bugs) | Reasoning effort flags respected, streaming delta compatibility, correct billing attribution |
| **Tool-scoping / intelligent tool selection** | Gemini CLI (#24246 — 128 tool limit), Codex (implied in parallel subagent issues) | Limit tool set per task, avoid context bloat from unused MCP tools |

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot CLI |
|---|---|---|---|---|
| **Primary focus** | Plugin/hooks ecosystem + enterprise reliability | Infrastructure stabilization + Rust alpha migration | Security posture (A2A) + automation pipeline (SSR) | Model configuration flexibility + day-to-day UX |
| **Target users** | Power users, plugin developers, multi-account teams | Linux desktop users, prompt engineers, MCP integrators | Security-conscious teams, compliance-heavy workflows | Enterprise teams, BYOK adopters, multi-agent orchestrators |
| **Technical approach** | JS/TS plugin architecture, hookify system, sandbox isolation | Rust rewrite, Noise protocol, MCP connection manager | Node.js with Ink UI, A2A server, Firestore-based automation | Agents convention, O runtime, GitHub ecosystem integration |
| **Strengths** | Largest plugin ecosystem; strong community documentation PRs | Fastest iteration velocity; robust sandboxing; cross-environment proxy support | Strong security focus (RCE prevention, workspace trust); event-driven architecture | Best model flexibility; .agents convention; GitHub-native workflows |
| **Community pain points** | Fable 5 billing chaos; session resume fragility; Windows/Linux parity | Linux desktop gap; token amplification; macOS pet space-jacking | Silent failures; subagent permission erosion; hang/deadlock issues | BYOK quality gaps; stale session memory leaks; MCP OAuth token handling |

**Key differentiators:**
- **Claude Code** leads on **ecosystem extensibility** (plugins, hooks) but struggles with **billing transparency** from the Fable 5 rollout.
- **OpenAI Codex** is the most **infrastructure-focused**, with daily Rust alpha releases and MCP/sandbox improvements, but the **Linux desktop gap** (804👍, 7 months old) is a growing liability.
- **Gemini CLI** is investing heavily in **security and automation** (A2A server hardening, headless PR generation pipeline) — appealing to enterprise but suffering from **silent failure modes** that erode user trust.
- **GitHub Copilot CLI** has the **smoothest model flexibility** and GitHub integration, but **BYOK integration fragility** and **memory management issues** (460MB heap leaks) are blocking enterprise adoption.

---

## 5. Community Momentum & Maturity

| Tool | Community Energy | Iteration Pace | Maturity Signals | Risk Indicators |
|---|---|---|---|---|
| **Claude Code** | **High** — 669👍 on account switching, 151 comments; plugin PRs show active third-party development | **Weekly stable** — v2.1.216 today with critical fix | Strong issue-to-PR correlation; documentation quality improving rapidly | Fable 5 billing bugs (4+ separate issues) signal rollout process gaps |
| **OpenAI Codex** | **Very high** — 804👍 on Linux desktop; 183 comments; 15+ PRs/day | **Daily alpha** — 4 releases in 24h with no changelogs | MCP infrastructure maturing; sandbox improvements robust | Changelog opacity; Linux desktop neglect risks power-user exodus |
| **Gemini CLI** | **Moderate** — issues show engagement but lower vote counts | **Nightly builds** — 1 release/day, automated | Security posture is industry-leading (A2A RCE prevention) | Silent failures (#22323, #28351) undermine user confidence; subagent permission erosion |
| **GitHub Copilot CLI** | **Moderate** — 12 new triage items today but lower comment counts | **Weekly/bi-weekly patches** — 2 releases in 24h | .agents ecosystem growing; BYOK infrastructure shows enterprise ambition | PR pause today; memory leaks (#4199) and clipboard regression (#3622) unresolved |

**Maturity assessment (subjective):**
- **Claude Code** and **OpenAI Codex** are at **early mainstream adoption** — large communities, well-defined workflows, but significant friction points (billing, platform gaps).
- **GitHub Copilot CLI** is at **early growth** — strong GitHub integration base, but memory/resource management and BYOK quality are immature.
- **Gemini CLI** is at **adolescence** — powerful security and automation features, but UX reliability (hangs, silent failures) needs work before broad adoption.

---

## 6. Trend Signals

1. **Plugin/Hooks Ecosystem is the New Battleground**: Claude Code alone shipped 8 hooks-related PRs today (import paths, UTF-8 encoding, shell quoting, documentation). The community is actively building, but **onboarding friction** (wrong marketplace names, broken URLs, silent failures on misnamed files) is the #1 barrier. Expect all tools to compete on plugin discoverability and developer experience.

2. **Billable Model Rollout is a Crisis Point**: Three of four tools had billing/model access issues today: Claude Code's Fable 5 misattribution (4 open bugs), Codex's GPT-5.6-sol Linux lockout (#32041), and Copilot CLI's BYOK reasoning effort rejection (#4012). **Model access transparency** and **correct billing attribution** are non-negotiable for enterprise trust.

3. **Silent Failures Are Eroding Trust**: Across tools, the most dangerous bugs are the ones users don't see — false success on subagent turn limits (Gemini #22323), clipboard copy silently failing (Copilot #3622), token amplification without notification (Codex #33196), and cache corruption from task_reminder nudges (Claude #78660). **Observability into agent behavior** (subagent queues, credit breakdowns, cache health) is becoming a core requirement.

4. **Cross-Platform Parity is a Dealbreaker**: Linux desktop support (Codex #11023, 804👍) and Windows clipboard/performance (Claude #62699, Copilot #3622) are the top-voted issues across tools. Teams with heterogeneous developer environments are evaluating tools based on their **weakest platform**, not their strongest.

5. **Security and Compliance Are Accelerating**: Gemini CLI's A2A server refactoring for RCE prevention (#28470) and Copilot CLI's agentStop hooks (#1.0.72) signal that **agent safety mechanisms** are maturing from opt-in to enforced. Expect all tools to add workspace trust enforcement, tool invocation auditing, and session isolation.

6. **The "Agent Orchestration" Pattern is Emerging**: Users want to chain agents, preserve context across subagent invocations, and monitor in-flight work — across all four tools. The market is moving beyond single-agent chat toward **multi-agent workflows** with coordination primitives (queues, shared state, inter-agent messaging).

7. **Memory and Context Management Remain Unsolved**: Claude Code's quadratic slowdown fix (#2.1.216), Copilot's 5MB CAPI limit (#4183), and Gemini's Auto Memory retry loop (#26522) all point to a shared challenge: **every tool is hitting fundamental limits** on how much context they can carry without performance degradation. This is the deepest technical problem facing the ecosystem.

---

*Report generated from community digest data dated 2026-07-21. All issue/PR references link to the respective public repositories.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data Date:** 2026-07-21 | **Source:** github.com/anthropics/skills

---

## 1. Top Skills Ranking

The following pull requests attracted the most community discussion and represent the most-watched Skill proposals:

### #1298 — fix(skill-creator): run_eval.py always reports 0% recall
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/1298)
The highest-activity PR targets the skill-creator's evaluation pipeline. It fixes `run_eval.py` reporting `recall=0%` for every skill description, installs the evaluation artifact as a real skill, and addresses Windows stream reading and parallel worker issues. Discussion centers on the breadth of the fix (trigger detection, Windows compatibility, parallel execution) and its criticality—without it, the description-optimization loop optimizes against noise. The PR references issue #556 with 10+ independent reproductions of the same bug.

### #514 — Add document-typography skill
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/514)
Introduces typographic quality control for AI-generated documents, targeting orphan word wrap, widow paragraphs, and numbering misalignment. The community discussion notes these issues affect virtually every Claude-generated document and that users rarely request typography fixes explicitly, making this a high-value silent quality improvement. Debated trigger specificity and whether rules should be configurable per document type.

### #1367 — feat(skills): add self-audit — mechanical verification + four-dimension reasoning quality gate (v1.3.0)
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/1367)
A universal auditing skill that performs mechanical file verification followed by a four-dimension reasoning audit in damage-severity priority order. Discussion highlights its model-agnostic design and the novel "Step 0" mechanical verification (confirming every claimed output file exists). Community interest centers on whether this overlaps with existing governance skills and how to handle false positives from the reasoning audit.

### #486 — Add ODT skill — OpenDocument text creation and template filling
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/486)
Provides full ODT/ODS support including document creation, template filling, and ODT-to-HTML conversion. Discussion focuses on the breadth of triggers—any mention of "ODT," "ODS," "ODF," "OpenDocument," or "LibreOffice"—and whether this duplicates existing PDF/DOCX skill patterns. The community requested clearer separation between ODT creation and conversion workflows.

### #525 — Add pyxel skill for retro game development
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/525)
Adds a skill wrapping `pyxel-mcp`, an MCP server for the Pyxel retro game engine. Covers the full workflow: write code → run and capture → inspect → iterate. Discussion centers on whether MCP-server-backed skills represent a new pattern in the ecosystem and how to handle dependency management when the skill requires external services. The author (@kitao) is the original Pyxel creator, lending credibility.

### #723 — Add testing-patterns skill
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/723)
Comprehensive testing coverage including philosophy (Testing Trophy model), unit testing (AAA pattern), React component testing, E2E, integration, and visual regression. Discussion highlights the trade-off between comprehensiveness and token cost, with some participants suggesting splitting into multiple focused skills. The "what NOT to test" guidance received particular praise.

### #83 — Add skill-quality-analyzer and skill-security-analyzer to marketplace
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/83)
Meta-skills that evaluate other skills across five quality dimensions and security vulnerabilities. Discussion reveals debate about whether meta-skills should live in the main repository or a separate tooling repository. The community expressed concern about these being distributed under the anthropic/ namespace (echoing issue #492).

### #210 — Improve frontend-design skill clarity and actionability
**Status:** Open | [GitHub](https://github.com/anthropics/skills/pull/210)
Revises the existing frontend-design skill for clarity and actionability, ensuring every instruction is executable within a single conversation. Discussion focuses on the tension between prescriptive guidance and creative flexibility. The community appreciated the explicit "what to avoid" sections added to the skill.

---

## 2. Community Demand Trends

From the most-discussed Issues, the community's top anticipated skill directions are:

### Security & Trust Boundaries
**Issue #492** (43 comments, 2 👍) — The single most-discussed issue in the repository. Community members are alarmed that community-contributed skills are distributed under the `anthropic/` namespace, creating a trust boundary vulnerability where users may grant elevated permissions to skills they believe are official. This has spawned calls for:
- A formal security review process for new skills
- Clear namespace separation (e.g., `anthropic-community/`)
- Permission scoping at the skill level

### Skill-Creator Reliability
**Issues #556** (12 comments, 7 👍), **#1169** (3 comments, 1 👍), **#1061** (3 comments, 2 👍) — The `run_eval.py` / `run_loop.py` pipeline is widely broken. Multiple independent users report:
- 0% trigger rate across all queries (`claude -p` never invokes skills)
- Windows compatibility failures (subprocess, encoding, pipe handling)
- The optimization loop returns the original description, making it non-functional for improving skill descriptions

This is the highest-priority infrastructure concern: the skill-creator toolchain is effectively broken for many users.

### Organizational Skill Sharing
**Issue #228** (14 comments, 7 👍) — Users need skills to be shareable within organizations without manual file transfers. Requested features include a shared skill library, direct sharing links, and org-wide default skills. This indicates enterprise adoption pressure.

### Duplicate Skill Conflicts
**Issue #189** (6 comments, 9 👍) — Installing both `document-skills` and `example-skills` plugins installs identical skills, causing duplicates in Claude Code's context window. The community wants clear documentation of what each plugin contains and deduplication logic.

### Governance & Safety Patterns
**Issue #412** (6 comments) — Proposed skill for agent governance including policy enforcement, threat detection, trust scoring, and audit trails. Indicates demand for production-grade safety tooling as Claude Code usage scales.

### Cross-Platform/Service Integration
- **SharePoint Online document handling** (Issue #1175, 4 comments) — Security and context window concerns
- **AWS Bedrock compatibility** (Issue #29, 4 comments) — Need to make skills work with hosted Claude via Bedrock
- **MCP exposure** (Issue #16, 4 comments) — Desire to expose skills as MCP endpoints

---

## 3. High-Potential Pending Skills

These PRs have active comment threads and are not yet merged, suggesting they may land soon:

| PR | Skill | Key Feature | Status Signal |
|----|-------|-------------|---------------|
| [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit | Mechanical verification + 4-dimension reasoning quality gate | Updated 2026-07-02, active discussion |
| [#1302](https://github.com/anthropics/skills/pull/1302) | color-expert | Color naming systems, spaces, harmony rules | Updated 2026-06-12, clean implementation |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | Full testing stack coverage | Updated 2026-04-21, large scope |
| [#525](https://github.com/anthropics/skills/pull/525) | pyxel | Retro game dev via MCP server | Updated 2026-07-15, author is Pyxel creator |
| [#181](https://github.com/anthropics/skills/pull/181) | SAP-RPT-1-OSS predictor | Tabular foundation model for SAP data | Updated 2026-03-16, niche but high-value |

The self-audit skill (#1367) has the strongest momentum—it addresses the widely-felt need for output quality guarantees, a gap the community has flagged across multiple threads. The testing-patterns skill (#723) and pyxel skill (#525) represent popular content creation domains.

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand at the Skills level is for infrastructure reliability of the skill-creator toolchain itself**—the `run_eval.py` 0% recall bug (#1298, #556, #1169) and cross-platform compatibility gaps (#1061, #362, #361, #538, #539, #541) dominate PR activity and issue discussions, indicating that the ecosystem's growth bottleneck is not lack of skill ideas (which are abundant) but rather the inability to reliably validate, test, and iterate on skill descriptions, especially on Windows environments.

---

# Claude Code Community Digest — July 21, 2026

## Today's Highlights

A new release (v2.1.216) rolls out a critical quadratic slowdown fix for long sessions alongside a new `sandbox.filesystem.disabled` setting. The community is experiencing severe turbulence around Fable 5 billing and authentication on Max plans, with multiple high-engagement issues open from yesterday's rollout. A flurry of documentation and encoding fixes are converging in the PR queue, addressing long-standing plugin and hooks usability problems.

## Releases

**[v2.1.216](https://github.com/anthropics/claude-code/releases/tag/v2.1.216)** — released today

- **`sandbox.filesystem.disabled`** setting: Allows users to skip filesystem isolation in sandbox mode while retaining network egress control — useful for workflows that need local file access without sacrificing outbound restrictions.
- **Critical performance fix**: Resolved a quadratic slowdown in long sessions where message normalization cost scaled with the square of the number of turns, causing multi-second stalls and slow session resumes.

## Hot Issues (Top 10 by Community Impact)

1. **[#18435 — Account profile switching in Claude Desktop](https://github.com/anthropics/claude-code/issues/18435)**  
   *Enhancement | 151 comments | 669 👍*  
   The highest-reacted open issue by a wide margin. Users managing multiple Claude accounts (e.g., work + personal) want seamless profile switching in the desktop app. This has been open since January with sustained interest — a clear signal for the product team.

2. **[#62699 — No clipboard copy in Claude Code TUI on Linux](https://github.com/anthropics/claude-code/issues/62699)**  
   *Bug | 32 comments | 47 👍*  
   `Ctrl+Shift+C` and right-click context menus fail to copy output text. A fundamental UX gap for Linux users that has drawn significant attention over the past two months.

3. **[#79337 — Fable 5 prompts "usage credits required" on Max plan](https://github.com/anthropics/claude-code/issues/79337)**  
   *Bug | 12 comments | 1 👍*  
   First-day crisis: Fable 5 launched as standard on Max plans, but Claude Code silently downgrades to Opus 4.8 and claims Fable requires credits. Affected users on the most expensive tier are getting the wrong model with no clear error. Community frustration is high.

4. **[#73597 — Opus subagents billed as Fable usage](https://github.com/anthropics/claude-code/issues/73597)**  
   *Bug | 5 comments*  
   Cost tracking bug where subagent usage is misattributed to Fable 5 regardless of the actual model. For teams monitoring budgets, this makes cost allocation unreliable.

5. **[#79516 — Fable 5 dialog contradicts documented plan inclusion](https://github.com/anthropics/claude-code/issues/79516)**  
   *Bug | 1 comment | 1 👍*  
   Model-switch dialogs claim Fable 5 is "billed separately from your plan," directly contradicting official Max plan documentation. User confusion compounded by conflicting UI messaging.

6. **[#70159 — Token counter disappears on input focus](https://github.com/anthropics/claude-code/issues/70159)**  
   *Bug | 5 comments*  
   A UI regression that prevents users from monitoring real-time token burn rates. Previously closed as a duplicate of a different issue, the reporter has provided clear evidence of a distinct problem.

7. **[#76727 — Cross-session coordination for concurrent Claude Code sessions](https://github.com/anthropics/claude-code/issues/76727)**  
   *Enhancement | 3 comments*  
   Heavy automation users running multiple sessions against one working tree have no first-party coordination mechanism. The only existing primitive (PreToolUse deny hooks) has silent failure modes — a power-user pain point.

8. **[#69094 — Expose queued Workflow subagents to SDK/headless clients](https://github.com/anthropics/claude-code/issues/69094)**  
   *Enhancement | 4 comments | 1 👍*  
   When Workflow tools spawn parallel subagents, those in-progress invocations are invisible to SDK-based monitoring. Teams building automated pipelines need observability into pending work.

9. **[#78660 — task_reminder nudge rewrites cached history mid-tool-loop](https://github.com/anthropics/claude-code/issues/78660)**  
   *Bug | 1 comment*  
   A forensic audit of 37,860 requests across 200+ sessions found task_reminder nudges causing near-total cache rebuilds, with 29% of sessions double-writing the opening context. Serious cost implications for high-volume users.

10. **[#79791 — Remote-control sessions lost Task tools on 2026-07-21](https://github.com/anthropics/claude-code/issues/79791)**  
    *Bug | 0 comments*  
    Fresh regression: sessions launched via `claude.ai/code` remote control have no native Task tools (TaskCreate, TaskUpdate, etc.). Local CLI sessions are unaffected, but remote workflow users are blocked.

## Key PR Progress (Top 10)

1. **[#79647 — Fix hookify imports independent of plugin directory name](https://github.com/anthropics/claude-code/pull/79647)**  
   Resolves a fragile import path issue where hooks broke if the plugin directory wasn't literally named `hookify`. Fixes #69665.

2. **[#79645 — Read rule/transcript files as UTF-8 in hookify](https://github.com/anthropics/claude-code/pull/79645)**  
   Opens files with explicit UTF-8 encoding instead of platform default. On Windows (cp1252), shipped example rule files containing emoji and arrows were unreadable. Fixes #77270.

3. **[#79644 — Quote `${CLAUDE_PLUGIN_ROOT}` in hook commands](https://github.com/anthropics/claude-code/pull/79644)**  
   macOS plugin paths contain spaces (`~/Library/Application Support/...`), causing shell word-splitting and silent hook failures across multiple bundled plugins. Fixes #78490.

4. **[#79643 — Align commit-push-pr docs with actual behavior](https://github.com/anthropics/claude-code/pull/79643)**  
   Documentation claimed PR descriptions included branch log data, but the actual command only injects `git status`, `git diff HEAD`, and branch name. Fixes #79144.

5. **[#79642 — Correct marketplace name to claude-code-plugins](https://github.com/anthropics/claude-code/pull/79642)**  
   Plugin dev README instructed users to install from a nonexistent marketplace name. Fixes #70064.

6. **[#79640 — Use disable-model-invocation in Ralph Wiggum commands](https://github.com/anthropics/claude-code/pull/79640)**  
   Commands used an unrecognized frontmatter key; switches to the documented `disable-model-invocation` property. Fixes #79138.

7. **[#79620 — Text-to-speech read-aloud hook for accessibility](https://github.com/anthropics/claude-code/pull/79620)**  
   Production-ready TTS hook supporting Piper (Linux), system `say` (macOS), and PowerShell (Windows). Includes markdown extraction and code-skip heuristics. Addresses #79542.

8. **[#79636 — Add `hookify.` prefix to example rule filenames](https://github.com/anthropics/claude-code/pull/79636)**  
   Shipped example rule files lacked the mandatory `hookify.` prefix required by the rule loader, causing them to be silently ignored. Fixes #79143.

9. **[#79635 — Fix PR review toolkit Contributing section](https://github.com/anthropics/claude-code/pull/79635)**  
   Pointed users to a private repository that doesn't exist in this repo. The review agents actually live in-tree. Fixes #79137.

10. **[#78532 — GCP Gateway: optional internal ALB + PG16 fix](https://github.com/anthropics/claude-code/pull/78532)**  
    Two fixes for the GCP Terraform example: makes internal ALB optional, and fixes PG16+ Cloud SQL deployments that fail with default shared-core tiers. Infrastructure-level reliability improvement.

## Feature Request Trends

- **Multi-account management** (#18435, 669 👍): The dominant feature request — users want profile switching in the Claude Desktop app for work/personal separation.
- **Agent/Workflow observability** (#69094, #76727): Multiple requests for SDK-level visibility into subagent queues and cross-session coordination primitives.
- **Accessibility** (#79620): Growing interest in TTS and other assistive technology hooks for hands-free workflows.
- **Plugin/hooks ecosystem** (multiple PRs): A wave of documentation and encoding fixes signals the community is actively building with plugins but hitting onboarding friction.

## Developer Pain Points

1. **Fable 5 rollout chaos**: Multiple billing/authentication bugs from the July 20 launch — wrong model assignments, contradictory "billed separately" messages, and subagent misattribution. Max plan users are paying for a model they aren't receiving.

2. **Session resume fragility**: Tasks lost on `--resume`, task list UI not rendering after resume, and task_reminder causing cache corruption — session persistence is unreliable for multi-session workflows.

3. **Windows/Linux parity gaps**: Missing copy functionality in Linux TUI, missing Cowork tab on Windows, and platform-specific encoding bugs (cp1252) in hooks. Cross-platform experience remains uneven.

4. **Plugin/hooks discovery friction**: Documentation errors (wrong marketplace name, broken contributing links), unquoted path variables on macOS, and silent failures when rules are misnamed. The ecosystem is appealing but hard to get started with.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-21

## Today's Highlights

The Codex team shipped four new Rust alpha releases (v0.145.0-alpha.25 through .29) and landed a wave of 15+ infrastructure-focused PRs addressing proxy support, sandbox stability, and plugin management. The community remains vocal about Linux desktop app support (Issue #11023 has reached 804 👍 with 183 comments, now seven months old), while Windows users continue to report sandbox ACL and performance regressions. A cluster of new issues today highlights growing frustration with token amplification during parallel subagent use and unexpected data upload volumes.

## Releases

**rust-v0.145.0-alpha.25 – .29** — four rapid alpha iterations published in the last 24 hours. No detailed changelogs were provided beyond the release tags. The volume suggests active stabilization work ahead of a likely minor version bump.

## Hot Issues (Top 10)

1. **[#11023 – Codex desktop app for Linux](https://github.com/openai/codex/issues/11023)** (804 👍, 183 comments) — The highest-voted open feature request. Users on Linux remain unable to use the native desktop app; the community has been waiting since February. Many report that macOS performance issues (linked issue #10432) make the app unusable there as well, intensifying demand for a Linux build.

2. **[#28969 – Add setting to disable auto-resolve in 60 seconds for questions](https://github.com/openai/codex/issues/28969)** (147 👍, 49 comments) — CLI and Plan users want control over the automatic 60-second resolution timer for interactive questions. The lack of a config toggle forces users to race against the clock during complex planning sessions.

3. **[#28190 – `rg` (ripgrep) is blocked by macOS](https://github.com/openai/codex/issues/28190)** (79 👍, 49 comments) — macOS security hardening is blocking Codex's internal use of `rg`. Users on Pro subscriptions are seeing workflow interruptions; requires either notarization or an alternate search strategy.

4. **[#32041 – VS Code extension opens blank webview on Linux](https://github.com/openai/codex/issues/32041)** (47 comments) — The latest VS Code extension (26.5707.*) renders a blank webview on Linux. Rolling back to 26.5623 works but loses access to the newer `gpt-5.6-sol` model.

5. **[#23198 – Codex Desktop on Windows extremely slow](https://github.com/openai/codex/issues/23198)** (46 👍, 20 comments) — Reproducible day-to-day slowness isolated to the Windows app itself, not system load. Multiple users confirm the issue persists across updates.

6. **[#17229 – Windows App spawns orphan `git.exe` / `conhost.exe` processes](https://github.com/openai/codex/issues/17229)** (28 comments) — Repeated spawning of `git status --porcelain=v1` leaves orphaned processes. This impacts performance and task-switching on Windows.

7. **[#31839 – Keybinding to cycle configured models](https://github.com/openai/codex/issues/31839)** (7 👍, 8 comments) — Users want a TUI action to switch between a shortlist of models without leaving the session, analogous to the existing reasoning-effort cycling.

8. **[#33196 – Parallel subagents cause extreme token amplification](https://github.com/openai/codex/issues/33196)** (3 comments) — A detailed report showing that parallel subagent runs trigger repeated context compaction and massive token consumption. One 20-minute session consumed an unexpectedly large volume of tokens for a simple analysis task.

9. **[#34542 – Codex Desktop sent 1 GB+ during a small HTML task](https://github.com/openai/codex/issues/34542)** (2 comments, filed today) — Suspected repeated upload of reference images/video. For users on metered or tethered connections, this is a significant data-usage bug.

10. **[#34512 – Recursive remote cleanup can escape intended directory via PowerShell quoting](https://github.com/openai/codex/issues/34512)** (2 comments, filed today) — A security-adjacent bug where recursive `Remove-Item` escalation through nested shells escaped the intended target directory. No root-path safety stop prevented the escalation.

## Key PR Progress (Top 10)

1. **[#34551 – Simplify TUI restoration for external editor](https://github.com/openai/codex/pull/34551)** — Removes unused `RestoreMode` selection; the TUI now always restores the terminal while keeping raw mode enabled, matching its external-editor call site.

2. **[#34547 – Add reciprocal rank fusion skill selection](https://github.com/openai/codex/pull/34547)** — Introduces a new skill selector that combines weighted lexical and character n-gram rankings via reciprocal rank fusion, improving the relevance of skill suggestions.

3. **[#34544 – Size Noise handshake buffers to their messages](https://github.com/openai/codex/pull/34544)** — Allocates handshake buffers from actual message sizes instead of placing maximum-size arrays on the stack. A memory and stack-footprint improvement for the Noise protocol layer.

4. **[#34540 – Detach Git metadata commands from stdin](https://github.com/openai/codex/pull/34540)** — Sets stdin to null for Git metadata commands and fsmonitor probes, preventing them from inheriting an open input stream and hanging.

5. **[#34533 – Centralize compacted rollout item construction](https://github.com/openai/codex/pull/34533)** — Refactors session history compaction so that replacement history always matches the live history, fixing potential state divergence during compaction.

6. **[#34525 – Add step-scoped data to extension contributors](https://github.com/openai/codex/pull/34525)** — Introduces an `ExtensionData` store per `StepContext`, allowing extensions to use capabilities bound to the current sampling step rather than the entire session.

7. **[#34522 – Split MCP connection manager into focused modules](https://github.com/openai/codex/pull/34522)** — Refactors the MCP connection manager into `required.rs` (startup validation), `tool_catalog.rs` (tool listing and metadata), and the existing connection lifecycle code. Improves maintainability.

8. **[#34509 – Honor system proxy settings for remote plugins](https://github.com/openai/codex/pull/34509)** — Remote plugin catalog, mutation, sharing, upload, and bundle download requests now respect Codex's effective outbound proxy policy and PAC routing.

9. **[#34497 – Preserve custom arg0 for sandboxed exec-server processes](https://github.com/openai/codex/pull/34497)** — Sandbox wrappers were stripping the `ExecParams.arg0` override. This PR routes sandboxed Unix launches with a custom `arg0` through to the inner process.

10. **[#30866 – Fix: reconcile loaded thread history on resume](https://github.com/openai/codex/pull/30866)** — A server-side fix by a core contributor (steipete-oai) that reconciles idle thread state with persisted rollout when `thread/resume` is called, preserving live overlay during active turns.

## Feature Request Trends

- **Linux Desktop App (#11023)** remains the single most-requested feature by a wide margin, with 804 👍 and 183 comments spanning seven months.
- **Model switching in TUI (#31839)** — users want keyboard-driven model cycling without leaving the session, mirroring the existing reasoning-effort toggle.
- **Configurable auto-resolve timeout (#28969)** — demand for a setting to disable or extend the 60-second automatic resolution of interactive questions, especially during complex planning.
- **Plugin/Skill separation (#21425)** — users want installed plugins separated from per-session skill metadata injection to avoid confusion between repo-local and cached skills.
- **`/restart` command (#33370, now closed)** — a proposal for an in-session restart command to avoid manual exit/relaunch was merged, indicating the team is responsive to CLI QoL improvements.

## Developer Pain Points

- **Windows sandbox and performance** (#14585, #30445, #23198, #34318) — ACL setup failures, UAC loops, and general slowness continue to plague Windows users. The sandbox setup helper can fail after UAC elevation, and trivial VS Code commands on Windows incur ~19-second delays.
- **Authentication failures on Windows** (#26764, #30746) — OAuth token exchange fails repeatedly on the Microsoft Store version of the app, blocking login after updates.
- **Context compaction and fork bugs** (#26739, #27894) — Forking from a pre-compaction message uses the compacted state instead of the original, and `/goal` mode replays the last manual steer instead of the intended goal.
- **Token/data amplification** (#33196, #34542) — Parallel subagents can cause extreme token consumption, and the desktop app may re-upload large reference files (images, video) repeatedly, consuming excessive bandwidth.
- **Model availability disparity** (#32041) — Newer VS Code extensions that break on Linux force users to roll back and lose access to `gpt-5.6-sol`. The `create_thread` tool advertises models it then rejects (#34532).
- **Pet overlay macOS space-jacking** (#23163) — The Codex pet forces macOS to auto-switch back to Codex's Space, making multi-Space workflows impossible while the pet is active.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-21

## Today's Highlights
The team continues to make heavy investments in the **A2A server security posture** and an automated **PR generation pipeline** (SSR), with multiple large PRs landing today. Meanwhile, a **critical authentication regression** in VS Code Agent Mode is being addressed, and the community continues to flag recurring reliability issues with **subagent lifecycle management** and **shell execution hangs**. The nightly release `v0.52.0-nightly.20260721` is out with no user-facing changes noted beyond the version bump.

## Releases
- **v0.52.0-nightly.20260721.gacae7124b** — Automated nightly bump. No user-facing changelog.  
  [Full diff](https://github.com/google-gemini/gemini-cli/compare/v0.52.0-nightly.20260720.gacae7124b...v0.52.0-nightly.20260721.gacae7124b)

## Hot Issues (10 selected)

1. **#22323 — Subagent recovery after MAX_TURNS falsely reports success**  
   A `codebase_investigator` subagent hits its turn limit, does zero analysis, yet reports `status: "success"` with `Termination Reason: "GOAL"`. This is a **classic silent failure** — users won't know their subagent got interrupted. 12 comments, high engagement.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/22323)

2. **#28351 — CLI silently halts when API returns empty "STOP" finishReason**  
   After a tool call, the backend returns `finishReason: "STOP"` with zero characters. The CLI hangs. This is a **critical UX blocker** because the user gets no error feedback. 6 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/28351)

3. **#21409 — Generalist agent hangs forever**  
   Simple tasks like folder creation cause the generalist agent to hang indefinitely. Workaround: instruct the model not to use subagents. 7 comments, 8 👍 — one of the **most upvoted bugs this week**.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/21409)

4. **#25166 — Shell command execution gets stuck "Waiting input" after completion**  
   Even trivial shell commands hang, showing "Awaiting user input" after the command finishes. Recurring frustration. 4 comments, 3 👍.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/25166)

5. **#21968 — Gemini does not use skills and sub-agents enough**  
   Custom skills (gradle, git) are ignored unless explicitly instructed. A common **adoption friction point** for power users trying to customize their agent. 6 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/21968)

6. **#22186 — "get-shit-done" output hook causes crash**  
   Near the end of output, the CLI crashes with no recovery. A **stability regression** affecting users who rely on this workflow. 3 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/22186)

7. **#22093 — Subagents running without permission since v0.33.0**  
   Users who disabled subagents in all configs still see them invoked. A **permission/configuration enforcement bug** that undermines user control. 3 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/22093)

8. **#26522 — Auto Memory retries low-signal sessions indefinitely**  
   Auto Memory only marks a session as processed after the extraction agent reads it. If the agent skips a low-signal session, it gets **re-surfaced repeatedly** — causing noise and wasted tokens. 5 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/26522)

9. **#22745 — Assess AST-aware file reads, search, and mapping (EPIC)**  
   Epic tracking whether AST-aware tools can reduce turns and token waste. If successful, this could **dramatically improve agent efficiency** in large codebases. 7 comments.  
   [View issue](https://github.com/google-gemini/gemini-cli/issues/22745)

10. **#24246 — 400 error when > 128 tools available**  
    API rejects requests with too many tools. The agent lacks tool-scoping logic. Expected: smarter tool selection. 3 comments.  
    [View issue](https://github.com/google-gemini/gemini-cli/issues/24246)

## Key PR Progress (10 selected)

1. **#28470 — fix(a2a-server): enforce workspace trust and task isolation to prevent RCE**  
   Large security fix. Refactors startup sequence and environment loading to prevent **zero-click RCE** in untrusted workspaces.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28470)

2. **#28472 — fix(core): verify cached credentials and restore GCA Agent Mode fallback**  
   Resolves a **critical auth regression** causing VS Code Agent Mode to exit with `FatalAuthenticationError`.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28472)

3. **#28388 — fix(core): scope tools.core wildcard deny to built-in tools**  
   A `tools.core` deny rule was silently disabling all MCP tools. This PR adds `builtinOnly` policy scoping to fix the over-blocking.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28388)

4. **#28389 — fix(core): add real-world time budget to prevent infinite-loop agent state transitions**  
   Adds a shared deadline to prevent event-driven agents from spinning indefinitely. A **stability improvement** for long-running sessions.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28389)

5. **#28397 — fix(core): remove synchronous I/O from shell tool critical path**  
   Replaces `fs.mkdtempSync`/`fs.existsSync` with async alternatives to fix **Ink UI stuttering and frame drops** during shell execution.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28397)

6. **#28394 — fix(core): remove temp files on background process exit**  
   Fixes a **temporary directory leak** left behind by background shell commands.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28394)

7. **#28386 — fix(vscode): track activation disposables**  
   Fixes #27790 where VS Code extension activation disposables were only partially tracked due to a comma-expression bug.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28386)

8. **#28469 — fix(core): rotate session ID on model fallback**  
   When falling back to `gemini-2.5-flash`, the CLI now rotates the session ID to avoid API errors ("Please submit a new query").  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28469)

9. **#28319 — refactor(a2a-server): enforce path trust check prior to environment loading (CLOSED)**  
   Earlier iteration of the A2A security fix, now closed in favor of #28470. Large refactor using `AsyncLocalStorage` for task isolation.  
   [View PR](https://github.com/google-gemini/gemini-cli/pull/28319)

10. **#28435 + #28433 + #28431 + #28434 + #28432 — SSR PR Generator Pipeline (5 PRs)**  
    A coordinated set of PRs introducing a new **headless PR generation pipeline**: Firestore locking, Antigravity agent runner, Cloud Run infrastructure, environment config parser, and GitHub API client. Large-scale infrastructure addition.  
    [View #28435](https://github.com/google-gemini/gemini-cli/pull/28435) | [#28433](https://github.com/google-gemini/gemini-cli/pull/28433) | [#28431](https://github.com/google-gemini/gemini-cli/pull/28431) | [#28434](https://github.com/google-gemini/gemini-cli/pull/28434) | [#28432](https://github.com/google-gemini/gemini-cli/pull/28432)

## Feature Request Trends

- **Tool-scoping and intelligent tool selection**: Multiple issues ask the agent to limit the tool set per task (e.g., #24246 — 128 tool limit, #23571 — random temp script creation). Expect smarter tool filtering soon.
- **AST-aware code understanding**: EPICs #22745 and #22746 explore AST-based file reads, search, and codebase mapping — a potential **big leap in code understanding efficiency**.
- **Subagent trajectory visibility**: Users want to inspect and share subagent behavior via `/chat share` (#22598) and `/bug` reports (#21763).
- **Agent self-awareness**: Accurately reporting its own flags, hotkeys, and capabilities (#21432) is a recurring request to reduce user confusion.
- **Memory system improvements**: Deterministic redaction (#26525), invalid inbox patch quarantining (#26523), and low-signal session handling (#26522) all point to a desire for **more robust and quieter memory extraction**.

## Developer Pain Points

1. **Silent failures and false successes** — The most frustrating pattern: agents report "GOAL/success" after hitting turn limits (#22323), and the CLI halts on empty API responses without error (#28351).
2. **Agent hangs and deadlocks** — Generalist agent hangs (#21409), shell execution "Waiting input" (#25166), and crash-on-finish (#22186) create **unreliable interactive sessions**.
3. **Subagent permission erosion** — Since v0.33.0, subagents run even when disabled in config (#22093). Users feel they've lost control.
4. **Memory extraction noise** — Auto Memory retrying low-signal sessions (#26522) and logging secrets before redaction (#26525) waste tokens and raise privacy concerns.
5. **Customization doesn't stick** — Custom skills and sub-agents are ignored unless explicitly prompted (#21968), undermining the value of user-defined tooling.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-07-21

---

## 1. Today's Highlights

Two patch releases (v1.0.72 and v1.0.73) landed yesterday, fixing a blocking loop in `agentStop` hooks and improving Anthropic subagent behavior with additional directories. The community is heavily focused on model configuration pain points—BYOK issues, context window bloat, and subagent model defaults dominate the new issue landscape, with 12 new triage items filed today alone.

---

## 2. Releases

**v1.0.73** (2026-07-20)
- [Release](https://github.com/github/copilot-cli/releases/tag/v1.0.73)
- Anthropic subagents now continue working when additional directories are configured
- Relative links in custom agent instructions are resolved from the agent file location

**v1.0.72** (2026-07-20)
- [Release](https://github.com/github/copilot-cli/releases/tag/v1.0.72)
- Fixed an infinite loop in `agentStop` hooks—CLI now ends the turn after 8 consecutive blocks
- `agentStop` hooks receive a `stop_hook_active` flag to detect forced continuation and self-limit
- Added opt-in git and gh authentication inside the O runtime

---

## 3. Hot Issues (10 Noteworthy)

1. **[#1481 – SHIFT+ENTER executes instead of line break](https://github.com/github/copilot-cli/issues/1481)** (CLOSED, 27 comments, 17 👍)
   - *Why it matters:* This UX inconsistency frustrated daily terminal users. Standard keystroke behavior (SHIFT+ENTER for newline) was overridden; resolved after months of community pressure.

2. **[#3622 – Copy to clipboard silently fails on Windows](https://github.com/github/copilot-cli/issues/3622)** (OPEN, 4 comments, 4 👍)
   - *Why it matters:* A regression from v1.0.48 that breaks a core workflow for Windows developers. The error is invisible—clipboard just stops updating.

3. **[#2193 – Default model for /fleet subagents](https://github.com/github/copilot-cli/issues/2193)** (OPEN, 3 comments, 13 👍)
   - *Why it matters:* Users must repeatedly specify model preferences in every prompt when using fleet subagents. High community demand for global/project-level defaults.

4. **[#4012 – BYOK reasoning effort bug with glm-5.2](https://github.com/github/copilot-cli/issues/4012)** (OPEN, 2 comments, 12 👍)
   - *Why it matters:* BYOK configurations reject valid `--reasoning-effort max` flags. Affects users bringing custom models—a growing segment.

5. **[#4183 – Auto-compaction doesn't prevent 5 MB CAPI limit](https://github.com/github/copilot-cli/issues/4183)** (OPEN, 1 comment, 3 👍)
   - *Why it matters:* Even with auto-compaction, tool-heavy sessions hit a hard 5 MB serialized request limit. Critical for long-running agentic workflows.

6. **[#4208 – Inline custom agent invocation and chaining](https://github.com/github/copilot-cli/issues/4208)** (OPEN, 0 comments, 3 👍)
   - *Why it matters:* Users want to invoke specific agents mid-prompt while preserving context. Enables complex multi-agent orchestration without losing state.

9. **[#4207 – Per-subagent AI credit breakdown in /usage](https://github.com/github/copilot-cli/issues/4207)** (OPEN, 0 comments, 5 👍)
   - *Why it matters:* Teams need visibility into which agents consume credits. Currently only aggregate session totals are shown.

10. **[#4202 – view tool reports "Path does not exist" in v1.0.73](https://github.com/github/copilot-cli/issues/4202)** (OPEN, 0 comments, 0 👍)
    - *Why it matters:* A regression introduced in 1.0.72/73 that breaks file reading for existing files. Critical blocker for file-based workflows.

11. **[#4199 – Stale sessions run old binary after in-CLI update](https://github.com/github/copilot-cli/issues/4199)** (OPEN, 0 comments, 0 👍)
    - *Why it matters:* Multi-tab users unknowingly run deleted binaries. Sessions hold ~460 MB heap for hours with no trimming.

12. **[#3125 – MCP tools/list_changed not visible mid-turn](https://github.com/github/copilot-cli/issues/3125)** (OPEN, 1 comment, 0 👍)
    - *Why it matters:* MCP server tool changes during a turn are invisible to the model until the next user message. Breaks dynamic tool discovery.

13. **[#4203 – Remote MCP OAuth: no silent refresh_token grant](https://github.com/github/copilot-cli/issues/4203)** (OPEN, 0 comments, 0 👍)
    - *Why it matters:* Expired access tokens force full interactive re-auth despite cached refresh tokens. Violates RFC 6749 §6; breaks automated sessions.

---

## 4. Key PR Progress

No pull requests were updated in the last 24 hours.

---

## 5. Feature Request Trends

Several clear themes emerge from today's issues:

1. **Agent orchestration** – Users want inline agent invocation, chaining, and context-preserving multi-agent workflows (Issue #4208)
2. **Model configuration flexibility** – Rapid model switching, preset profiles, and per-agent model defaults are repeatedly requested (Issues #2193, #4190)
3. **Enterprise and billing visibility** – Per-subagent credit breakdowns and billing entity selection are blocking enterprise adoption (Issues #4207, #4005)
4. **MCP ecosystem maturity** – Better OAuth token handling, dynamic tool discovery, and registry policy overrides are needed for MCP integration (Issues #3125, #4203, #4205)
5. **.agents ecosystem expansion** – Extending the `.agents` convention to cover instructions, hooks, and agents in any folder (Issue #4204)

---

## 6. Developer Pain Points

- **BYOK quality barriers** – Two separate BYOK issues (#4012, #4196) show custom model integration is fragile, with reasoning effort bugs and streaming delta failures
- **Windows clipboard regression** – Issue #3622: a silent failure that persists across releases, eroding trust in copy functionality
- **Memory and session management** – Stale sessions holding 460 MB heap (#4199), completed background agents being purged too quickly (#2595), and auto-compaction not preventing hard 5 MB limits (#4183) indicate systemic memory/resource management gaps
- **Terminal input inconsistencies** – SHIFT+ENTER (#1481, now closed) and Ctrl+G failing during clarifying questions (#4198) show keyboard handling remains a pain point across platforms
- **Hard-coded assumptions** – Issue #4194 ("Severe levels of hard-coding: Frustrating") signals growing developer frustration with inflexible internal logic
- **File system regressions** – The `view` tool regression (#4202) in v1.0.73 suggests test coverage gaps for core file operations

</details>

---

## Closed-Source Tools

> Version tracking only (source: npm registry / official changelog). No public repo; each maps to a mainstream model vendor.

| Tool | Vendor / Model | Latest | Published | Status |
| --- | --- | --- | --- | --- |
| CodeBuddy | Tencent · Hunyuan 混元 | `2.125.0` | 2026-07-21 | 🆕 New |
| MiniMax Code | MiniMax · MiniMax M1 | `1.0.18` | 2026-07-16 | — |
| ZCode | Zhipu · GLM | `3.3.6` | 2026-07-15 | — |


---
*This digest is auto-generated by [agents-radar](https://github.com/7ky-bk/agents-radar).*