# OpenClaw Ecosystem Digest 2026-07-21

> Issues: 50 | PRs: 50 | Projects covered: 4 | Generated: 2026-07-21 14:17 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw Deep Dive

# OpenClaw Project Digest — 2026-07-21

## Today's Overview

OpenClaw shows **high activity** with 50 issues and 50 PRs updated in the last 24 hours, signaling a robust development pace. The project is processing significant community contributions and bug reports, though the large volume of open issues (48 open vs 2 closed) indicates a growing backlog. No new releases were published today. The issue tracker reveals a dual focus: a wave of automated P2/P3 bug reports from a single contributor covering memory leaks, security vulnerabilities, and performance regressions, alongside real user reports of session-state corruption and hook delivery failures.

## Releases

**No new releases today.** The last published version appears to be `2026.7.1`, which is referenced in several bug reports. A significant release-blocking issue (#107347) was noted: a Chinese-language localization package `@qingchencloud/openclaw-zh@2026.7.1-zh.1` contains a `workspace:*` protocol dependency that breaks `npm install` for external users.

## Project Progress

**6 PRs were merged or closed today**, reflecting active maintenance. Key closures include:

- **[#105162 — fix(anthropic): accept "cli" entrypoint in Claude session catalog discovery](https://github.com/openclaw/openclaw/pull/105162)** — Merged. Resolves a bug where Claude Code v2.x sessions (which write `entrypoint: "cli"`) were invisible in OpenClaw's session catalog, which only recognized `"sdk-cli"`. User-facing fix for macOS session discovery.

- **[#112234 — [Bug]: plugins list --json reports an unobserved empty agentHarnessIds array](https://github.com/openclaw/openclaw/issues/112234)** — Closed by maintainer. A metadata-snapshot display issue that did not affect runtime behavior.

- **[#105164 — Claude Code v2.x sessions not showing in session catalog](https://github.com/openclaw/openclaw/issues/105164)** — Closed (resolved by the merged PR above).

Several large feature PRs are open and progressing:
- **#112176** — Adds channel-owned setup contracts, removing core's need to understand plugin-specific fields
- **#112260** — Ships user-facing session observer HUD and sidebar for the web Control UI
- **#111527** — Major config-surface reduction tranche 3 with product consolidation decisions pending

## Community Hot Topics

Most active conversations and highest-reaction issues:

1. **[#84527 — [Feature]: Add Antigravity CLI (agy) as CLI backend](https://github.com/openclaw/openclaw/issues/84527)** — **11 👍, 5 comments.** High community demand following Google's I/O announcement that Gemini CLI is being deprecated. Users need a migration path before the June 18 cutoff. This is a **time-sensitive roadmap item** as the deprecation date has already passed (June 18, 2026).

2. **[#53408 — [Bug]: Write/exec tool parameters silently dropped after long conversations](https://github.com/openclaw/openclaw/issues/53408)** — **9 comments, 2 👍.** A P1 "platinum hermit" severity bug where `write` and `exec` tools silently drop all parameters after 15+ turns. This is a **critical session-state corruption issue** that undermines agent reliability in long-running tasks.

3. **[#9607 — Himalaya skill: missing email formatting philosophy and incorrect command syntax](https://github.com/openclaw/openclaw/issues/9607)** — **5 comments.** A long-standing documentation gap (since February) needing product decision. Highlights friction in email skill usability.

4. **[#106172 — [Experiment]: Using AI to security-check AI outputs](https://github.com/openclaw/openclaw/issues/106172)** — **2 👍.** A proposal for a "Publish Guardian" layer to reduce hallucination/noise in AI outputs. Signals community interest in output quality assurance.

5. **[#109065 — [Feature]: Integration with Alexa and Google Home](https://github.com/openclaw/openclaw/issues/109065)** — **1 👍.** User request for voice assistant integration, reflecting demand for natural spoken-language interaction.

## Bugs & Stability

### Critical (P0) Bugs
- **[#106588 — [Bug]: VPN NEEDED users](https://github.com/openclaw/openclaw/issues/106588)** — P0, crash-level. Users in restricted regions (e.g., Iran) cannot download or use OpenClaw without VPN. No fix PR. *Release-blocker UX issue.*
- **[#107347 — @qingchencloud/openclaw-zh contains workspace:* protocol dependency](https://github.com/openclaw/openclaw/issues/107347)** — P0, release-blocker. Published package breaks `npm install`. Requires immediate package.json fix.

### High-Severity (P1) Bugs
- **[#53408 — Write/exec tool parameters silently dropped](https://github.com/openclaw/openclaw/issues/53408)** — P1, session-state corruption. No fix PR identified. **Most impactful open bug** — agents become unusable after prolonged tool use.
- **[#111498 — Main agent blocked by persistent workspace-state migration](https://github.com/openclaw/openclaw/issues/111498)** — P1, regression. macOS agents refuse Anthropic turns due to stale workspace-state migration.
- **[#108287 — fix(sqlite): allow verified shared wal backports](https://github.com/openclaw/openclaw/pull/108287)** — P1 fix PR open for SQLite WAL corruption handling.

### Medium-Severity (P2) Bugs
- **Memory and performance bugs** — A wave of 20+ issues filed by a single author (aniruddhaadak80) between July 13-14, covering:
  - [#107520 — Race condition on event-ledger log rotation](https://github.com/openclaw/openclaw/issues/107520) — Data loss under high concurrent load
  - [#107531 — Privilege escalation via mock environment overrides](https://github.com/openclaw/openclaw/issues/107531) — Security, needs review
  - [#106687 — Hook injection payload size limit bypass](https://github.com/openclaw/openclaw/issues/106687) — OOM risk (crash-loop impact)
  - [#106679 — Infinite fallback loop on generic provider errors](https://github.com/openclaw/openclaw/issues/106679) — Crash-loop when all providers fail
  - [#106669 — Unbounded memory growth in context-engine caching](https://github.com/openclaw/openclaw/issues/106669) — Heap exhaustion
  - [#112309 — announce-path delivery silently drops MEDIA attachment on iMessage](https://github.com/openclaw/openclaw/issues/112309) — New today, attachments lost on iMessage
  - [#112307 — Kubernetes deployment uninstalling crudely deletes namespace](https://github.com/openclaw/openclaw/issues/112307) — Regression, causes complete service loss
  - [#111683 — Windows Tray regenerates device identity on every reboot](https://github.com/openclaw/openclaw/issues/111683) — Requires re-pairing each boot
  - [#111549 — Duplicate outbound message delivery to WhatsApp](https://github.com/openclaw/openclaw/issues/111549) — Duplicate messages with different provider IDs
  - [#112304 — WeChat channel session permanently stuck after tool failure](https://github.com/openclaw/openclaw/issues/112304) — Chinese WeChat users cannot recover without `/new`

### Today's New Bugs
- [#112309 — iMessage MEDIA attachment drop](https://github.com/openclaw/openclaw/issues/112309)
- [#112307 — Kubernetes namespace deletion regression](https://github.com/openclaw/openclaw/issues/112307)
- [#112304 — WeChat session stuck after tool failure](https://github.com/openclaw/openclaw/issues/112304)
- [#112238 — Channel setup vocabulary leaking into core](https://github.com/openclaw/openclaw/issues/112238) — Maintainer-identified design debt

## Feature Requests & Roadmap Signals

### Likely for Next Release
1. **[Antigravity CLI (agy) backend](https://github.com/openclaw/openclaw/issues/84527)** — High community priority. Google has deprecated Gemini CLI; users need migration *urgently*. This is likely being actively worked on.
2. **[Channel-owned setup contracts (PR #112176)](https://github.com/openclaw/openclaw/pull/112176)** — Large architectural improvement; in active review. Would move channel-specific vocabulary out of core.
3. **[Session observer HUD and sidebar (PR #112260)](https://github.com/openclaw/openclaw/pull/112260)** — User-facing feature already landed server-side, now shipping UI. Expected in `2026.7.2`.

### Roadmap Signals
- **SMS provider abstraction** ([#110723](https://github.com/openclaw/openclaw/issues/110723)) — Plivo as first alternative to Twilio. Signals growing multi-provider strategy.
- **Image-to-video generation** ([#108568](https://github.com/openclaw/openclaw/issues/108568)) — Adding video generation providers beyond text-to-video.
- **Voice assistant integration** ([#109065](https://github.com/openclaw/openclaw/issues/109065)) — Alexa/Google Home, indicating ambition toward ambient computing.
- **AG-UI channel** ([#109203](https://github.com/openclaw/openclaw/pull/109203)) — Protocol for CopilotKit-style browser UIs. Third-party contribution; could be next release candidate.
- **AI output quality guard** ([#106172](https://github.com/openclaw/openclaw/issues/106172)) — "Publish Guardian" concept for hallucination reduction. Experimental but signals user pain.

## User Feedback Summary

**Pain Points:**
- **Session reliability** is the #1 user frustration. Long conversations (>15 turns) silently break tool parameters (issue #53408). Agents get permanently stuck after single tool failures (WeChat #112304). These are session-state corruption issues that destroy user trust.
- **Geographic restrictions** (#106588) block users in sanctioned regions from even downloading OpenClaw, affecting ~90M potential users in Iran alone.
- **iMessage attachment handling** is unreliable: the hook system doesn't fire for session replies (#112027), and attachments are silently dropped on announce-path deliveries (#112309).
- **Windows ecosystem** has a fundamental pairing issue: device identity is regenerated on every reboot (#111683), forcing users to re-pair their tray app daily.
- **Installation confusion** persists: different install scripts default to different Node versions (#79558), and the Chinese localization package (#107347) is broken on npm.

**Satisfaction Signals:**
- **AG-UI integration** (#109203) — An external creator built a full bridge between AG-UI and OpenClaw, showing the plugin system's extensibility is valued.
- **Email skill documentation** (#9607) — Users are actively trying to use Himalaya skill, indicating the email integration is important even if docs need improvement.
- **Cron alert improvements** (#80246) — Users requested better failure alerting, and a fix PR has been waiting for author review since May.
- **Token usage API** (#8635) — Users want programmatic budget tracking, showing production usage at scale.

## Backlog Watch

### Urgent — Needs Maintainer Decision
- **[#84527 — Antigravity CLI backend](https://github.com/openclaw/openclaw/issues/84527)** — Google deprecation has already taken effect (June 18). **Must act now** to prevent existing users from losing CLI access.
- **[#53408 — Write/exec tool parameters dropped](https://github.com/openclaw/openclaw/issues/53408)** — P1 open since March 24. No fix PR. Critical for any production deployment.

### Long-Standing Without Maintainer Review
- **[#9607 — Himalaya skill formatting & syntax](https://github.com/openclaw/openclaw/issues/9607)** — Since February 5 (167 days). Labeled `needs-product-decision` and `needs-maintainer-review`.
- **[#8635 — Token Usage API for session_status](https://github.com/openclaw/openclaw/issues/8635)** — Since February 4 (168 days). `needs-maintainer-review` and `needs-product-decision`.
- **[#79558 — Clarify Node defaults between install scripts](https://github.com/openclaw/openclaw/issues/79558)** — Since May 8 (74 days). Stale, with linked PR open.

### Blocking Release (P0)
- **[#107347 — Chinese localization package broken](https://github.com/openclaw/openclaw/issues/107347)** — `workspace:*` dependency in published package. Blocks all Chinese users from npm install.
- **[#106588 — VPN needed for restricted regions](https://github.com/openclaw/openclaw/issues/106588)** — P0 crash bug, blocks users in Iran and similar regions.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided community digest summaries.

---

### Cross-Project Ecosystem Report: Personal AI Agent Open-Source Landscape

**Date:** 2026-07-21

---

### 1. Ecosystem Overview

The open-source personal AI agent ecosystem is experiencing a period of intense development, characterized by high community activity and a critical focus on reliability and production readiness. A clear divide is emerging between established projects like OpenClaw, which are grappling with legacy stability issues and a growing maintenance burden, and rapidly evolving competitors like NanoBot and ZeroClaw, which are shipping large architectural changes. Common pain points across the ecosystem reveal that session state management, security boundaries for sub-agents, and robust multi-platform channel support are the primary technical hurdles that need to be solved for agents to move beyond novelty and into reliable daily use. The community is also signaling a strong demand for better local model support, standardized APIs, and easier deployment for non-technical users.

### 2. Activity Comparison

| Project | Open Issues (24h) | Open PRs (24h) | PRs Merged/Closed (24h) | Recent Release | Health Score (Summary) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 48 | 50 | 6 | `2026.7.1` (stale) | **Moderate/Concerning** – High activity but a growing backlog (48 open issues) and multiple critical (P0) release blockers. |
| **NanoBot** | 3 (11 updated) | 17 (39 updated) | 22 | None today | **Good/Healthy** – Strong, focused engineering with high PR throughput and responsive maintainer engagement. |
| **Hermes Agent** | 47 | 46 | 4 | v0.19.0 (Yesterday) | **Moderate (Post-Release Stress)** – High activity and community growth, but with significant regressions and a fragile session state subsystem. |
| **ZeroClaw** | 50 | 47 | 3 | None today | **Moderate/Strained** – Intense development velocity with a focus on security and architecture, but a zero-issue-closure count suggests a triage bottleneck. |

**Note on Health Score:** This is a qualitative assessment based on the balance of feature work, bug fixes, backlog management, and release stability.

### 3. OpenClaw's Position

OpenClaw remains the dominant reference implementation in the ecosystem, acting as a core proving ground for a vast array of features from CLI backends to voice assistant integration. Its primary advantage is its extensive community and feature matrix, but this also creates significant technical debt. Compared to peers, OpenClaw is absorbing a larger volume of bug reports, including an automated wave of security and performance issues, indicating a critical need for architectural hardening. While Hermes Agent has a massive community surge with its v0.19.0 release, and ZeroClaw is actively modernizing its architecture with WASM plugins, OpenClaw appears to be in a more reactive "firefighting" mode. Its community is the largest and most demanding, but its maintenance overhead is proportionally higher, creating a risk of stagnation if the P0/P1 bugs are not addressed swiftly.

### 4. Shared Technical Focus Areas

Several demanding requirements are emerging across multiple projects, signaling key pain points for the entire ecosystem:

- **Session State Integrity (All Projects):** Every project is battling issues related to session corruption. **OpenClaw** (write/exec tool parameters dropped), **Hermes Agent** (blank sessions, cost data loss, stale prompts), and **ZeroClaw** (MCP memory leaks) all suffer from this. It is the single most critical technical debt item for the industry.
- **Security Boundaries for Sub-Agents (OpenClaw, ZeroClaw, NanoBot):** The concept of delegating tasks to sub-agents (or "delegates") is creating new attack surfaces. **OpenClaw** has injection bypass issues, **ZeroClaw**'s `delegate` bypasses tool allowlists, and **NanoBot** is implementing a "guarded tool gateway." This is a fundamental security challenge for multi-agent architectures.
- **Channel & Platform Reliability (OpenClaw, ZeroClaw, Hermes Agent):** All projects show a push for more channel integrations (Matrix, Teams, WeChat, Telegram), but this comes with reliability problems. **OpenClaw** reports iMessage attachment drops and WeChat session stalls. **ZeroClaw** has a blocked Telegram channel. **Hermes Agent** has cross-session message routing bugs.
- **Local Model Performance (NanoBot, OpenClaw):** The community for **NanoBot** is vocal about unusably slow local inference with Ollama, and **OpenClaw** is rushing to support the Antigravity CLI due to Google's Gemini CLI deprecation. This indicates a deep need for efficient, local-first inference as a fallback and for advanced users.
- **Deployment & Onboarding Friction (All Projects):** From **OpenClaw**'s broken npm packages in China to **ZeroClaw**'s rejected config templates and **Hermes Agent**'s Windows init timeouts, a significant portion of bug reports relate to "first-run" and configuration pain.

### 5. Differentiation Analysis

| Feature | OpenClaw | NanoBot | Hermes Agent | ZeroClaw |
| :--- | :--- | :--- | :--- | :--- |
| **Primary Focus** | Broad feature set & community reference | Stability & local LLM performance | Desktop-first experience & community scale | Security, architecture, & enterprise features |
| **Target User** | End-users & plugin developers | Power users & local-first enthusiasts | Desktop-centric users & contributors | Advanced users & enterprise adopters |
| **Architecture Approach** | Monolithic with high plugin surface | Focused, lean core with active maintenance | Large, rapidly expanding codebase | Modernizing via WASM runtime plugins |
| **Key Strength** | Feature breadth, ecosystem size | Responsive maintainers, fast bug fixes | Large community, massive contributor base | Strong security thinking, clean architecture |
| **Key Weakness** | High backlog, session corruption | Low on-boarding features (e.g., Dokploy) | Post-release regressions, Windows parity | Triage bottleneck, author-blocked PRs |

### 6. Community Momentum & Maturity

- **Rapidly Iterating (High Momentum, Post-Stabilization):** **NanoBot** is in a healthy "sprint" phase, merging a high volume of PRs across security, features, and polish. It appears more stable and responsive than its peers.
- **Post-Release Chaotic (High Momentum, High Instability):** **Hermes Agent** has the highest community energy with its v0.19.0 release, but is in a reactive phase, dealing with regressions and a fragile session state. This is typical of a major release but requires a fast patch cycle to maintain trust.
- **Architecture Modernization (High Momentum, Structural Shift):** **ZeroClaw** is undergoing a deep architectural transformation (WASM plugins, security sandboxes). It has high activity but a lower closure rate, suggesting a focus on getting the foundation right. It appears to be building for long-term resilience.
- **Stabilizing Under Load (Moderate Momentum, High Risk):** **OpenClaw** is processing a massive volume of issues and feature requests but is showing signs of strain with a growing backlog and unresolved critical bugs. It needs a focused "stabilization release" to address its fundamental reliability problems or it risks losing developer trust to faster-moving peers.

### 7. Trend Signals

- **The End of "Sessions as Infinite Chat":** The most critical trend is the failure of the simple, endless chat session model. Users demand persistent, durable, and bounded sessions. This is driving features like ZeroClaw’s "Goal Mode" and the universal struggle with state corruption. The winner will be the project that can treat sessions as reliable, resumable, and finite transactions.
- **Security is Moving from Edge-Case to Core Feature:** The ecosystem is realizing that agents are not just chatbots but execution engines. The work on guarded tool gateways, delegate allowlists, and avoiding plaintext API keys shows that security is no longer an afterthought but a core architectural requirement for production deployments.
- **The Split Between Cloud and Local:** We are seeing a clear divergence in user needs. Most projects focus on cloud LLMs, but a large, vocal minority is demanding efficient local model support (NanoBot’s community is a clear example). The ability to seamlessly switch between cloud and local will be a key differentiator.
- **Developer Experience is the New Moat:** Initial setup is a major pain point. Projects that can offer frictionless "getting started" experiences (simple `install`, single file configs, pre-built templates) will have a significant advantage in attracting and retaining developers, especially as the user base expands beyond core AI enthusiasts.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-21

## Today's Overview
NanoBot saw high activity today with 11 issues updated (8 closed) and 39 PRs updated (22 merged/closed), indicating a strong pulse of collaborative maintenance. No new releases were published today, but the repository is processing a significant volume of bug fixes, security patches, and feature work concurrently. The project is showing signs of a focused engineering sprint, with several high-priority (p1) PRs moving through review and merge cycles.

## Releases
No new releases were published today.

## Project Progress
22 pull requests were merged or closed today, reflecting substantial forward movement across several areas:

- **Security & Stability**: Multiple critical fixes landed, including `fix(files): reject oversized reads before loading` ([PR #5014](https://github.com/HKUDS/nanobot/pull/5014)) which prevents OOM crashes from multi-GB files, and `fix(security): validate each shell segment against exec.allowPatterns` ([PR #4562](https://github.com/HKUDS/nanobot/pull/4562)) closing a command injection bypass.
- **Config & Persistence**: `fix(config): write config.json atomically via temp+replace` ([PR #4984](https://github.com/HKUDS/nanobot/pull/4984)) prevents truncated config files on crash. `fix(transcription): resolve ${VAR} env refs in transcription api_key/api_base` ([PR #4989](https://github.com/HKUDS/nanobot/pull/4989)) fixes voice transcription authentication.
- **Provider Enhancements**: `feat(providers): support Codex fast mode` ([PR #5019](https://github.com/HKUDS/nanobot/pull/5019)) adds OpenAI Codex priority tier support. `fix(providers): sanitize UTF-16 surrogates at provider request boundary` ([PR #4952](https://github.com/HKUDS/nanobot/pull/4952)) fixes emoji-heavy content crashes.
- **WebUI Polish**: Multiple PRs improved markdown rendering, autocomplete behavior, and diff display ([PR #5016](https://github.com/HKUDS/nanobot/pull/5016), [PR #5015](https://github.com/HKUDS/nanobot/pull/5015)).
- **Channel Integration**: `feat(channels): add guarded tool gateway` ([PR #5006](https://github.com/HKUDS/nanobot/pull/5006)) closes issue [#4911](https://github.com/HKUDS/nanobot/issues/4911), enabling channels to run agent tools under proper security context.
- **Subagent Stability**: `fix(subagent): cascade exec session termination on /stop` ([PR #5021](https://github.com/HKUDS/nanobot/pull/5021)) prevents orphaned child processes when subagents are cancelled.

## Community Hot Topics

1. **[Issue #4867](https://github.com/HKUDS/nanobot/issues/4867) (CLOSED) — Ollama caching** — This enhancement request about preserving exact prompt prefixes for Ollama cache saw 22 comments and strong engagement. The underlying need is performance: users report 60-second delays per turn with local models on 32GB VRAM setups, making the system "totally unusable." The community is demanding efficient local LLM inference.

2. **[Issue #4864](https://github.com/HKUDS/nanobot/issues/4864) (OPEN) — Endless tool_call loop** — With 1 👍 and 4 comments, this bug describes an infinite loop where `complete_goal` fails because the gateway mis-serializes parameters. The underlying issue appears to be a recent regression in tool parameter handling, causing persistent failure cycles that require gateway restarts.

3. **[Issue #4911](https://github.com/HKUDS/nanobot/issues/4911) (CLOSED) — Guarded tool gateway for channels** — With 1 👍 and 1 comment, this enhancement was so well-received that it was quickly implemented in [PR #5006](https://github.com/HKUDS/nanobot/pull/5006), showing responsive maintainer engagement with community proposals.

## Bugs & Stability

### Critical Severity
- **OOM crash on large file reads** ([Issue #4785](https://github.com/HKUDS/nanobot/issues/4785)): `read_file` loads entire files into memory before truncation, causing OOM on multi-GB files. **Fix merged today** in [PR #5014](https://github.com/HKUDS/nanobot/pull/5014) with a 100 MiB pre-read cap.
- **Endless tool_call loop on serialization regression** ([Issue #4864](https://github.com/HKUDS/nanobot/issues/4864)): Gateway parses recap parameter as bare string instead of JSON object. **Open**, with no fix PR yet identified.

### High Severity
- **Session message list unbounded growth** ([Issue #4787](https://github.com/HKUDS/nanobot/issues/4787)): `Session.messages` never trims stored messages despite `FILE_MAX_MESSAGES=2000` cap. **Closed** but no fix PR visible.
- **Orphaned child processes on gateway shutdown** ([Issue #4794](https://github.com/HKUDS/nanobot/issues/4794)): Exec sessions lack cleanup hooks. **Closed** — fix assumed in [PR #5021](https://github.com/HKUDS/nanobot/pull/5021) for subagents.
- **BaseException catch blocks KeyboardInterrupt/SystemExit** ([Issue #4788](https://github.com/HKUDS/nanobot/issues/4788)): Tool runner catches `BaseException`, preventing clean shutdown. **Closed** — fix in [PR #4811](https://github.com/HKUDS/nanobot/pull/4811) is a start but doesn't fully address the `BaseException` scope.

### Medium Severity
- **Shell execution lacks user confirmation** ([Issue #5013](https://github.com/HKUDS/nanobot/issues/5013)): Chinese-language request for human-in-the-loop confirmation before shell execution. **Closed** — likely being addressed via the shell guard improvements.
- **QQ channel WebSocket reconnect spam** ([Issue #4767](https://github.com/HKUDS/nanobot/issues/4767)): Fixed 5-second reconnect with no backoff floods logs. **Closed**.
- **API keys stored as plaintext** ([Issue #4803](https://github.com/HKUDS/nanobot/issues/4803)): `ProviderConfig.api_key` lacks `exclude=True`, so keys appear in config dumps. **Still open** after 15 days.

## Feature Requests & Roadmap Signals

### Likely Next-Release Candidates
- **Model presets bound to sessions** ([PR #4866](https://github.com/HKUDS/nanobot/pull/4866)): Persisting model overrides per-session is open with 0 conflicts resolved — a strong candidate for the next release.
- **ModelScope provider support** ([PR #4965](https://github.com/HKUDS/nanobot/pull/4965)): Adding support for open-source model inference via ModelScope's API. Likely to merge given the trend toward multi-provider support.
- **Actual fallback model display** ([PR #5017](https://github.com/HKUDS/nanobot/pull/5017)): WebUI enhancement showing the real model used after fallback — addresses a common user confusion point.
- **Skill explicit context loading** ([PR #5018](https://github.com/HKUDS/nanobot/pull/5018)): Allowing direct callers to preload specific skills rather than only `always: true` skills.

### Longer-Term Signals
- **Dokploy template** ([Issue #1503](https://github.com/HKUDS/nanobot/issues/1503)): Open for over 4 months, requesting a deployment template for non-technical users. Low activity suggests it may not be a priority.
- **Ollama caching optimization** ([Issue #4867](https://github.com/HKUDS/nanobot/issues/4867)): While closed, the intense discussion (22 comments) signals that local model inference performance is a major community pain point that may lead to more systematic caching improvements.

## User Feedback Summary

**Pain Points:**
- Local model inference with Ollama is unusably slow (60s delays per turn) — the most vocal dissatisfaction surface today.
- Shell commands execute without user confirmation, creating security concerns especially for non-technical users.
- Configuration file corruption risk if write is interrupted mid-operation.
- Voice transcription fails with HTTP 401 due to missing env-var interpolation.
- WebUI session metadata doesn't persist across restarts for sessions with legacy file paths.

**Positive Signals:**
- Community proposals like the guarded tool gateway are being implemented rapidly, showing strong maintainer responsiveness.
- Unicode/emoji handling improvements demonstrate attention to real-world input diversity.
- Multiple Chinese-language contributions (issues, PRs) indicate growing international community engagement.

## Backlog Watch

| Issue/PR | Days Open | Priority | Status |
|----------|-----------|----------|--------|
| [Issue #1503](https://github.com/HKUDS/nanobot/issues/1503) — Dokploy template | 139 days | Enhancement | No maintainer response |
| [Issue #4803](https://github.com/HKUDS/nanobot/issues/4803) — API keys stored as plaintext | 15 days | Security | No fix PR, no assignee |
| [PR #4594](https://github.com/HKUDS/nanobot/pull/4594) — Shell guard for `=` path delimiter | 22 days | Priority p1, Security | Open, needs review |
| [PR #4866](https://github.com/HKUDS/nanobot/pull/4866) — Model presets bound to sessions | 11 days | Feature, p1 | Open with conflicts |
| [PR #4963](https://github.com/HKUDS/nanobot/pull/4963) — WebUI polish | 4 days | Feature | Open with conflicts |

The **API keys in plaintext** issue ([#4803](https://github.com/HKUDS/nanobot/issues/4803)) is the most concerning long-standing security vulnerability, as it exposes credentials to anyone with filesystem access. The **Dokploy template** request ([#1503](https://github.com/HKUDS/nanobot/issues/1503)) has received no maintainer attention in over 4 months, which may reflect either low priority or a need for community contributions to move it forward.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — July 21, 2026

## Today's Overview

Hermes Agent v0.19.0 "Quicksilver Release" shipped yesterday, representing the largest single release in the project's history with over ~2,245 commits and ~450 new community contributors since v0.18.0. Activity remains extremely high, with 50 active issues and 50 open PRs updated in the last 24 hours — indicating a vibrant but complex maintenance landscape. The project closed 3 issues and merged 4 PRs today, while community engagement continues at peak levels with several long-running feature branches still in review. Notably, a substantial portion of current activity centers on session state management, multi-platform gateway support (Matrix, Telegram, Discord), and addressing Windows-specific stability issues.

## Releases

**v2026.7.20 — Hermes Agent v0.19.0 (The Quicksilver Release)** was released on July 20, 2026. This is a major version bump from v0.18.0, encompassing approximately 300,000 lines added and 36,000 removed across 2,465 files. Key highlights: ~3,300 issues closed since v0.18.0, 450+ community contributors, and 1,065 merged PRs. No explicit breaking changes or migration notes have been published yet, though the project's release note ("Hermes is the mess") suggests the team is aware of rough edges. Given the scale, users upgrading from v0.18.x should expect configuration and plugin compatibility validation.

## Project Progress

Four PRs were merged today:

- **#68639 (CLOSED)** — `fix(desktop): ⌘W closes visible file tab when preview selection is stale` — resolves a macOS-specific keyboard shortcut behavior where closing via Command+W could appear to no-op while a file tab remained visible.
- **#68675 (CLOSED)** — `fmt(js): npm run fix auto-fix` — automated formatting cleanup, merged squash.
- **#68679 (OPEN, awaiting merge)** — `feat(openrouter): add policy-aware catalog and ZDR controls` — introduces policy-aware model catalog fetching and zero-data-retention controls for OpenRouter.
- **#68664 (OPEN)** — `fix(approval): restore session approval tier for tirith-flagged prompts` — fixes a regression across all messaging platforms where security-flagged prompts lost their session-level approval tier.

Long-running feature branches remain in play: the workspace binding security fix (#17938) and normalized channel identity (#17711) have been open since April but continue to receive updates.

## Community Hot Topics

**Most Commented:**

- **Issue #64182** (15 comments) — *Plugin Interface Expansion Tracking Issue* — This 7-day-old community-driven planning thread is synthesizing Discord feedback into a stable plugin expansion roadmap. The goal is to unblock contributors with long-queued PRs. It's the project's most active discussion this week, suggesting strong pent-up demand for plugin API stability.

- **Issue #38602** (13 comments, 50 👍) — *Desktop Client-Only Installation* — A long-standing feature request from June that asks for thin-client mode where the desktop app connects to a remote Hermes instance without bootstrapping a local runtime. With 50 upvotes, this is the highest-reaction issue in today's digest and represents a significant unmet user need for remote/hybrid workflows.

- **Issue #63078** (9 comments) — *First message in new session creates blank session* — A P1 bug affecting all new conversations on Desktop. The lack of clear reproduction steps and the "needs-decision" label suggest maintainers are still assessing root cause. High impact on user onboarding.

## Bugs & Stability

**Critical/Blocker:**

- **#67762 (P2, OPEN)** — `agent.session_estimated_cost_usd resets to $0 on gateway restart` — Labeled a "silent undercount" blocker for any feature displaying running session costs. The cost value is not rehydrated from SQLite after gateway restart. No fix PR attached yet; needs-decision label suggests architectural debate on whether to store transient cost state durably.

**High Severity (P1-P2):**

- **#63078 (P1, OPEN)** — Blank session on first message in Desktop. Affects all new users. Needs reproduction steps and decision.
- **#68358 (P2, OPEN)** — Cross-session message routing bug: Desktop messages routed into stale TUI session after TTFB timeout. Fix PR not yet linked.
- **#68369 (P2, OPEN)** — `hermes skills check` crashes on Chinese Windows due to UTF-8/GBK encoding mismatch in lock file loading. Low complexity fix expected (`open(..., encoding='utf-8')`).
- **#68484 (P2, OPEN)** — Windows git-install users on diverged feature branches receive misleading "1 commit behind" banner. PR #68677 exists to fix the tip-count reporting logic.
- **#68531 (P2, OPEN)** — `BaseEnvironment.__del__` runs cleanup/sync during interpreter shutdown on remote backends, risking incomplete file sync. Dangerous destructor pattern that could lose data.
- **#68559 (P2, OPEN)** — Multiplexed gateway ignores routed profile's terminal backend configuration; Docker profiles inherit incorrect sandbox settings. Security boundary concern.
- **#68609 (P2, OPEN)** — Windows Desktop agent initialization times out because a suspended git child probe blocks deferred session builds.
- **#68563 (P2, OPEN)** — Gateway durable sessions do not refresh system prompt after SOUL.md changes — a subtle session staleness bug.

**Medium Severity (P3):**

- Multiple TUI/Desktop rendering bugs: duplicate "Summarizing thread" timers (#68634), bottom menu jiggling from session timer (#68461), white flash on macOS dark mode (#68640).
- mem0 plugin regression: `custom_instructions` silently dropped since v2026.7.20 (#68625) — a fresh regression in the just-released version.
- Fireworks.ai model picker regression: Minimax M3 callable but missing from picker (#68628).
- Kanban unblock parses reason text as task IDs (#68613) — follow-up to a previously fixed issue.

## Feature Requests & Roadmap Signals

**Strong Community Demand:**

1. **Desktop Client-Only Installation** (#38602, 50 👍) — Thin-client mode remains the highest-demand feature. Likely candidate for v0.20.0 given sustained community interest and the project's plugin expansion roadmap.

2. **Command-F Session Search** (#68635, 2 comments, gained traction today) — macOS-native search within existing chat sessions. Small scope, high usability impact — could ship in a point release.

3. **Switch to Developer ID signing for macOS** (#68618) — Addresses TCC permission resets on every update due to adhoc signing. Developer ID signing is a prerequisite for distribution outside developer mode and for enterprise deployment.

4. **Mistral AI built-in provider** (#68588, just filed) — Community wants Mistral as a first-class selectable provider, not just via `custom_providers`. The frequent custom_provider complexity complaints suggest this may be prioritized.

**Roadmap Signals:**

- The *Plugin Interface Expansion* tracking issue (#64182) is laying groundwork for a new stable plugin contract. Expect this to influence v0.20.0 or an intermediate release.
- OpenRouter policy-aware catalog (#68679, waiting merge) signals deeper provider integration and rate-limit/no-data-retention controls for enterprise users.
- Multi-platform Matrix gateway features (PRs #61511, #61219, #61210) show sustained investment in messaging platform parity.

## User Feedback Summary

**Satisfaction:** The sheer scale of v0.19.0 (450+ new contributors, 3,300 issues closed) indicates a healthy, engaged community. Users are actively filing enhancement requests and reporting bugs, suggesting the project remains usable and well-loved.

**Pain Points:**

- **Session state management confusion** dominates bug reports today. Multiple bugs involve messages routing to wrong sessions (#68358, #64789), session cost data disappearing (#67762), stale system prompts (#68563), and blank sessions (#63078). The `sweeper:risk-session-state` label appears on at least 10+ issues today, indicating this is the project's most fragile subsystem.
- **Windows experience lags significantly.** Issues cover git installation confusion (#68484), encoding crashes (#68369), agent init timeouts (#68609), and update failures. The `platform/windows` and `sweeper:risk-platform-windows` labels are pervasive.
- **Desktop app stability regressions** with blank sessions, white flashes, and unresponsive UI after ~5 messages (#63047) suggest Electron-side performance optimization is needed.
- **Plugins/regressions from v0.19.0:** The mem0 plugin regression (#68625) and TUI reasoning indicator text leakage (#68600) are likely artifacts of the massive codebase change, and early adopters should expect patch releases.

## Backlog Watch

**Critical long-standing issues needing maintainer attention:**

- **PR #17938 (OPEN since April 30)** — Gateway workspace binding security guard. This 83-day-old PR is the oldest open feature branch with recurring updates. It blocks several downstream Matrix/gateway improvements and touches security-sensitive git command protection. Given its `sweeper:risk-security-boundary` label and current relevance to gateway multiplexing bugs (#68559), this deserves prioritization.

- **PR #17711 (OPEN since April 30)** — Expose normalized channel identity in gateway sessions. Same age as #17938, both by author `nepenth`. These two PRs appear to be part of an ongoing gateway architecture refactor.

- **Issue #39971 (OPEN since June 5)** — Desktop Profile list missing "switch/activate" action (Japanese-language report). 47 days without resolution. While P3, the lack of any response or labeling change suggests non-English bug reports may receive less attention.

- **Issue #39497 (OPEN since June 5)** — Desktop App: personality config ignored, slash commands blocked, app hangs after sleep. Written by an AI agent ("take this with a pinch of salt"), which may explain the lack of response despite describing three distinct bugs. The personality config issue may be related to the gateway's stale prompt problem (#68563).

**Assessment:** The project is in a healthy but strained state — massive community growth, a newly shipped major release, and a firehose of incoming issues. The session state subsystem is clearly the biggest technical debt area, and Windows parity remains an ongoing commitment gap. The v0.19.0 release will likely need a fast v0.19.1 patch cycle for the fresh regressions.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-21

## Today's Overview

ZeroClaw is in a period of intense development activity with 50 open issues and 47 open PRs updated in the last 24 hours. No new releases were published today. The project maintains a high velocity across bug fixing, RFC work, and feature implementation, with notable focus on security vulnerabilities, channel integration robustness, and architectural modernization. The three merged/closed PRs today indicate steady progress, though the zero-closed-issue count suggests maintainers are prioritizing triage and active discussion over closure.

## Releases

No new releases published in the last 24 hours.

## Project Progress

Three PRs were merged or closed today:
- **#9234** — `fix(web): render reasoning-only turns instead of hanging silently` — Gateway web chat no longer hangs when reasoning models (GLM, Qwen, DeepSeek) produce thinking content without assistant text; now committed as an assistant message.
- **#9233** — `fix(runtime/security): Prevent landlock locks zeroclaw itself` — Critical fix preventing the Landlock sandbox from locking the daemon process after the first sandboxed shell command.
- **#9241** — `feat(channels): add Microsoft Teams (Bot Framework) channel` — New channel integration enabling DM and @-mention interaction through Bot Framework, with JWT validation and Bot Connector API support.

## Community Hot Topics

1. **#8226** — `[Feature]: Add typed per-agent git identity for built-in git operations` (6 comments, 0 👍) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8226)  
   *Active discussion on runtime_context and runtime_secrets blocks for multi-tenancy. High architectural impact; likely needed for enterprise deployments.*

2. **#8505** — `[Bug]: Telegram channel cannot be configured` (6 comments, 0 👍) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8505)  
   *S1 severity bug blocking Telegram channel setup. User reports doctor claiming channels not set up after following quickstart. High frustration visible in related documentation bugs (#8810).*

3. **#8303** — `RFC: Goal mode for bounded autonomous session work` (4 comments, 1 👍) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8303)  
   *Most-liked issue today. Users want durable goal-oriented sessions with pause/cancel/failure semantics. Indicates strong demand for autonomous task management.*

4. **#8603** — `RFC: OpenAI Chat Completions compatibility adapter` (4 comments, 0 👍) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)  
   *Standardization demand: users want OpenAI-compatible API surface for tool/IDE integration. Gateway architecture interest.*

5. **#8850** — `Move optional channels & tools to runtime plugins` (4 comments, 0 👍) — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8850)  
   *Major architecture tracker to move from compile-time features to WASM plugins. Shrinks binary, enables dynamic extension.*

## Bugs & Stability

### Critical (S0 - data loss/security risk)
- **#8279** — `delegate bypasses parent's tool allowlist` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8279)  
  *Sub-agent can invoke tools the parent policy excludes. Active discussion; no fix PR yet. Security architecture concern.*

### High (S1 - workflow blocked / S2 - degraded behavior)
- **#8505** — `Telegram channel cannot be configured` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8505)  
  *Blocked Telegram onboarding. Runtime/daemon component. Related: #8810 documentation errors.*

- **#8642** — `MCP/tool-schema cloning drives unbounded RSS growth` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8642)  
  *Memory leak split from #5542 OOM tracker. In-progress; memory growth in agent loop.*

- **#8731** — `Stdio-based MCP servers accumulating as zombie processes` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8731)  
  *Zombie process accumulation. Fix PR #8948 open and needs author action.*

- **#8718** — `zeroclaw config init ships rejected config template` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8718)  
  *Fresh installs have silently broken voice transcription. High impact on onboarding.*

- **#8410** — `Channel tasks need first-class no-reply outcome` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8410)  
  *Conditional tasks send unwanted visible responses. UX degradation.*

### Medium (S2/S3)
- **#8720** — `Bedrock Nova 2 Lite cachePoint error` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8720)  
  *Provider-specific caching issue. In-progress workaround investigation.*

- **#8615** — `Compatible provider silently deletes content via <think> tag stripping` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8615)  
  *Content loss from aggressive regex. In-progress.*

- **#8834** — `config set can't create aliases outside providers.*` — [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8834)  
  *CLI usability bug blocking configuration of risk_profiles, peer_groups, channels.*

## Feature Requests & Roadmap Signals

### High Priority (likely next release)
- **#8226** — Per-agent git identity with runtime_context/runtime_secrets (accepted, risk:medium) — *Enterprise multi-tenancy building block.*
- **#8303** — Goal mode for bounded autonomous sessions (RFC, 1 👍) — *Strong community demand for durable task execution.*
- **#8603** — OpenAI Chat Completions adapter (RFC, in-progress) — *Standard API compatibility for ecosystem integration.*
- **#8850** — Runtime plugins via WASM (tracker, in-progress) — *Architecture modernization, shrinks binary.*

### Community-Requested Features
- **#8541** — Matrix thread-scoped history (accepted) — *Matrix power users want conversation boundaries.*
- **#8568** — Mixture-of-Agents (MoA) virtual provider (RFC) — *Multi-model perspective for hard tasks.*
- **#8780** — Realtime speech-to-speech channel for Gemini Live (RFC) — *Multimodal channel interest.*
- **#8415** — Telegram Bot API 10.1 Rich Messages (accepted) — *Better formatting in Telegram.*
- **#8600** — Easy per-chat model switching (accepted tracker, 1 👍) — *Provider flexibility demand.*
- **#8348** — Skill CRUD hooks/events (accepted) — *External system integration.*
- **#8309** — Wire up SkillForge or remove (accepted) — *Orphaned feature needs decision.*

## User Feedback Summary

**Positive signals:**
- Strong interest in architectural improvements (WASM plugins, MoA, OpenAI adapter) indicates active developer community.
- Microsoft Teams channel PR #9241 merged today — shows platform expansion.
- Language model reasoning render fix (#9234) addresses annoyance with reasoning-only models.

**Pain points:**
- **Onboarding friction:** Repeated reports of broken Telegram channel setup (#8505, #8810), rejected config templates (#8718), and config CLI usability issues (#8834, #9240, #9239, #9236).
- **Security concerns:** Delegate tool bypasses allowlists (#8279) and accumulated zombie processes (#8731) erode trust.
- **Memory/resource issues:** OOM from MCP tool cloning (#8642) and silent content deletion (#8615).
- **Documentation gaps:** Missing Bedrock credential setup guidance (#8925), insufficient SOP examples (#8587).
- **Windows support gaps:** config_save_isolation gate skips Windows tests (#9238), PowerShell not supported (#9182, in-progress).

## Backlog Watch

### Issues Needing Maintainer Attention
- **#8309** — `SkillForge (#144) is orphaned` — Created 2026-06-25, 2 comments. *Decision needed: wire up with safe defaults or remove. Stale for nearly a month with no clear path forward.*
- **#8410** — `Channel tasks need first-class no-reply outcome` — Created 2026-06-28, 3 comments. *S2 severity, affects all channels, no resolved action beyond discussion.*
- **#8587** — `Adding more SOPs examples to syntax` — Created 2026-07-01, 1 comment. *Documentation request with no maintainer response.*
- **#8720** — `Disable cachePoint for Bedrock Nova 2 Lite` — Created 2026-07-04, 3 comments. *Support request with active user frustration, in-progress but stale.*

### PRs with Stale `needs-author-action` Labels
Multiple PRs remain blocked on author response:
- #8438 (cron shell_output_format), #9075 (doctor model cache), #8948 (MCP zombie reaping), #8781 (security advisory cleanup), #9105 (memory timeout), #9114 (Landlock sandbox), #9182 (PowerShell support), #9194 (KeySource trait), #8979 (SOP channel gates), #8752 (OTel nesting), #8826 (SSRF gate), #9193 (credential error messages), #8674 (zerocode buffer fix).

These 13 PRs represent significant feature and bugfix work blocked on author engagement — a concern for release velocity.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/7ky-bk/agents-radar).*