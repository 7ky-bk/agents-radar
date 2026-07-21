# OpenClaw 生态日报 2026-07-21

> Issues: 50 | PRs: 50 | 覆盖项目: 4 个 | 生成时间: 2026-07-21 14:17 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw 项目深度报告

好的，作为AI智能体与个人AI助手领域开源项目分析师，现在根据OpenClaw项目2026年7月21日的GitHub数据，为您呈现今日项目动态日报。

---

# OpenClaw 项目动态日报 | 2026年7月21日

## 1. 今日速览

今日OpenClaw项目社区活跃度极高，共产生50条Issue和50条PR，反映出强大的开发者参与与用户反馈密度。核心焦点集中在**会话状态持久化**（#53408, #111498）、**插件与外部集成兼容性**（#9607, #84527, #111660）以及**大规模性能与内存泄漏**（#107550, #107517等）三大领域。值得注意的是，多位用户集中提交了关于性能、安全和架构重构的深度Bug报告，表明项目正在经历关键的质量打磨期。同时，PR提交和合并活动频繁，大型重构PR（如配置表面缩减#111527）和针对核心网关的修复（#103148）正在推进，项目整体处于“积极迭代、攻坚痛点”的健康状态。

## 2. 版本发布

- **无**。今日无新版本发布。

## 3. 项目进展

今日合并/关闭的重要PR数量为6个，以下是其中对项目健康度提升最显著的两个：

- **修复Claude Code会话发现**：PR #105162 (`[CLOSED]`) 已合并，修复了`entrypoint: “cli”`未被识别的问题。这解决了用户无法在OpenClaw控制UI中看到Claude Code v2.x会话的痛点，弥合了与其他AI工具的互操作性鸿沟。
- **注入消息归属权改进**：PR #79959 (`[CLOSED]`) 已关闭，允许通过`chat.inject` API覆盖提供商归属信息（`originAgent`）。这增强了开发者对注入消息的可追溯性和控制力，对开发高级集成场景至关重要。

**项目推进评估**：今日活动主要集中在巩固现有功能、解决报告较早的关键Bug（如#105164），并为大型架构重构（如#111527）争取更多审查与社区反馈。整体处于“清除积压、筹备大版本”的前夜阶段。

## 4. 社区热点

- **#84527 [Feature]: Add Antigravity CLI (agy) as CLI backend**：获得了 **11个👍** 和5条评论。这是社区对Google Gemini CLI即将被淘汰的积极反应。用户正在推动OpenClaw快速适配`agy`，以保证其核心CLI工作流的连续性。这反映了社区对**上游依赖变更**的高度敏感性和适应性。
    - [查看 Issue](https://github.com/openclaw/openclaw/issues/84527)
- **#53408 [Bug]: Write/exec tool parameters silently dropped after long conversations**：拥有9条评论和2个👍。用户报告了一个严重影响日常使用的“静默丢参数”Bug，引发了社区广泛讨论。这表明**会话上下文管理**是OpenClaw在实际使用中的最核心痛点之一，尤其对于专业用户。
    - [查看 Issue](https://github.com/openclaw/openclaw/issues/53408)
- **#112238 [maintainer] Channel setup vocabulary leaks into core**：由核心维护者提出的Issue，旨在将通道专有设置词汇从核心代码中解耦，归入插件。这代表了项目对**插件架构纯净性**的内省与改进，获得社区高度关注。
    - [查看 Issue](https://github.com/openclaw/openclaw/issues/112238)

## 5. Bug 与稳定性

今日Report的Bug问题呈现高度集中态势，尤其是来自用户 `aniruddhaadak80` 的历史性问题。按严重程度排序如下：

| 严重程度 | 问题标题 | 链接 | 是否有修复PR | 分析 |
| :--- | :--- | :--- | :--- | :--- |
| **P0 (Blocking)** | VPN NEEDED users | [#106588](https://github.com/openclaw/openclaw/issues/106588) | 无 | 地区封锁影响用户下载使用，是严重的**用户体验阻断**问题。 |
| **P0 (Blocking)** | `@qingchencloud/openclaw-zh` 包含workspace:*协议 | [#107347](https://github.com/openclaw/openclaw/issues/107347) | 无 | 发布的包存在依赖解析问题，是阻止国产化渠道用户安装的**严重Bug**。 |
| **P1 (Critical)** | Bug: Main agent blocked by persistent workspace-state migration | [#111498](https://github.com/openclaw/openclaw/issues/111498) | 无 | **回归问题**，核心Agent在macOS上完全被阻塞，威胁会话连续性。 |
| **P1 (Critical)** | Bug: Write/exec tool parameters silently dropped | [#53408](https://github.com/openclaw/openclaw/issues/53408) | 无 | 会话后续功能异常，属于长期未决的**高影响行为Bug**。 |
| **P2 (High)** | Bug: Windows Tray regenerates device identity on every reboot | [#111683](https://github.com/openclaw/openclaw/issues/111683) | 无 | 导致每次重启需重新配对，严重降低Windows用户持续使用体验。 |
| **P3 (Medium)** | Bug: Duplicate outbound message delivery to WhatsApp | [#111549](https://github.com/openclaw/openclaw/issues/111549) | 无 | 消息重复发送，影响通信可信度。 |
| **P3 (Medium)** | Bug: @openclaw/codex fails to register in CLI context | [#111870](https://github.com/openclaw/openclaw/issues/111870) | 无 | 重要的插件`codex`在CLI场景下崩溃，影响自动化工作流。 |
| **多种严重级别** | 若干关于性能、内存泄漏、安全及架构的Bug (Issues #107xxx, #106xxx系列) | 见数据概览 | 有多个关联的Lint/安全/架构PR | 这些集中在系统性技术债务上，今天反应量大，是项目健康度提升的“排毒”期。 |

## 6. 功能请求与路线图信号

- **✅ 高飞可能性**：
    - **集成Concentrate AI** (#106477)：希望添加类似OpenRouter的“零加价”AI模型路由服务。如果社区呼声高，可能进入P2或P3优先级。
    - **视频生成提供商** (#108568) 和 **语音助手集成** (#109065)：表明社区正在向多模态和家庭IoT领域探索，符合个人AI助手的未来发展方向。
- **❓ 观察中**：
    - **“发布卫士”安全层** (#106172)：用AI审核AI输出的噪声和幻觉，属实验性提案。虽有2个👍，但实施路径尚不明确，短期内路线图可能性低。
- **🚩 信号解读**：
    - **Pr #112176** (`feat(channels): add channel-owned setup contracts`): 直接将通道设置所有权从核心下放给插件，是解决 #112238 需求和实现架构层面的简化。这很可能是**下一个小版本**的核心特性。

## 7. 用户反馈摘要

- **核心满意度**：用户对OpenClaw的**扩展性**和**社区响应速度**有认可（如维护者快速推进CLI后端的适配提议#84527），并愿意提交高质量的重构提案（如#112238）。这表明项目的核心架构和协作模式是健康的。
- **核心痛点**：**会话稳定性**是用户最强烈的呼声。`write/exec`参数的静默丢失(#53408)、Agent被模块迁移卡死（#111498）、以及各种内存泄漏，严重影响了专业用户的信赖感。部分用户表达了对“用着用着突然出问题”的挫败感。
- **使用场景观察**：用户对**多平台消息通道**怀有极高热情，如微信（#112304、#107347）、iMessage（#112309）、WhatsApp（#111549）等。同时，对**跨平台文件共享**（SSRF、外部插件解析等）和安全配置（CRASH DUMP中的密钥泄露 #106674）表达了增长中的紧迫感。
- **用户体验反例**：
    - Windows Tray用户反馈设备密钥重置问题（#111683），直指客户端持久层缺陷。
    - Kubernetes用户投诉命名空间粗暴删除（#112307），暴露了部署脚本的非专业处理模式。

## 8. 待处理积压

以下为今日数据中发现的长时间未响应但影响重大的问题，需要维护者关注：

- **#53408 [Bug]: Write/exec tool parameters silently dropped** (`2026-03-24` 创建，`P1`，`needs-maintainer-review`)：一个持续近4个月、高影响的核心功能Bug，虽有9条评论但无进展。建议提升优先级并指定处理人。
    - [查看 Issue](https://github.com/openclaw/openclaw/issues/53408)
- **#79558 安装脚本Node默认版本冲突** (`2026-05-08` 创建，`stale`，`needs-product-decision`)：明确的产品决策Issue，关系到用户初次安装体验，但已“冷却”。建议尽快做出决策并更新文档。
    - [查看 Issue](https://github.com/openclaw/openclaw/issues/79558)
- **长期待回复的PR**：**#79985** (#79985, docs+tests: clarify agents.list visibility)、**#88709** (#88709, fix(auth): cooldown billing failures)、**#80246** (#80246, feat(cron): include event time)等8个PR状态为“等待作者更新”（`status: ⏳ waiting on author`）。其中多个含`stale`标签。他们代表着社区贡献者的持续耐心，维护者应主动联系作者或尝试接手，以防止贡献流失。
    - [查看待处理PR列表](https://github.com/openclaw/openclaw/pulls?q=is%3Aopen+is%3Apr+status%3A%E2%8F%B3+waiting+on+author)

---

## 横向生态对比

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将基于您提供的四个项目（OpenClaw、NanoBot、Hermes Agent、ZeroClaw）在 2026年7月21日的社区动态，为您呈现一份横向对比分析报告。

---

# 个人 AI 智能体开源生态横向对比报告 (2026-07-21)

## 1. 生态全景

2026年7月21日，个人AI智能体/自主智能体开源生态呈现出 **“分化演进、共性攻坚”** 的态势。一方面，各项目根据自身定位加速迭代，如 Hermes Agent 发布重大版本，NanoBot 快速修复安全漏洞，OpenClaw 和 ZeroClaw 则在为大规模重构铺垫；另一方面，所有项目都共同面临着**会话状态管理**、**安全与权限控制**、**多模态与外部集成**以及**架构模块化**等核心挑战。社区对**基础设施稳定性**和**平台扩展性**的呼声高过对基础功能的新增，表明生态正从“能用”向“好用、可靠”的成熟阶段迈进。

## 2. 各项目活跃度对比

| 项目 | 今日 Issues 数 | 今日 PR 数 | 版本发布 | 健康度评估 | 总体阶段 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 50 (新) | 50 (新) | 无 | **积极迭代，攻坚痛点** | 质量打磨期 |
| **NanoBot** | 11 (总) / 8 (关闭) | 39 (总) / 22 (关闭) | 无 | **补强与优化，效率高** | 快速迭代期 |
| **Hermes Agent** | 100 (总) | 100 (总) | **v0.19.0 “Quicksilver”** | **大步向前，但稳定性挑战大** | 快速迭代期 |
| **ZeroClaw** | 100 (总) | 47 (总) / 0 (合并) | 无 | **输入活跃，输出滞后** | 早期活跃期 |

*注：Issues/PRs 数量基于报告摘要中提及的“更新量”，可能包含历史数据，但仍反映当日社区活动热度。*

**健康度总结：**
- **NanoBot** 表现最优，社区贡献与维护者响应形成了正向循环，修复效率高。
- **Hermes Agent** 势头最猛，新版本发布带动了海量反馈，但新功能和Bug报告并存，对用户稳定性构成短期挑战。
- **OpenClaw** 处于中等水平，积压问题较多，但PR提交活跃，正在为下一个大版本做准备。
- **ZeroClaw** 最为激进，社区反馈和创新提案丰富，但核心代码合入速度滞后，长期来看可能形成技术债务。

## 3. OpenClaw 在生态中的定位

- **核心竞争力：** **开源核心参照**（OpenClaw是其他分支的代码上游），其社区规模庞大（单日50+ Issues/PRs），且拥有深厚的架构设计讨论（如配置表面缩减、插件架构纯净性）。这决定了 OpenClaw 是**行业标准制定者**和**生态基石**。
- **与技术分支对比：**
    - **vs Hermes Agent / NanoBot**：OpenClaw 的社区成熟度和设计讨论深度更高，而后者更侧重于具体功能的快速实现和问题修复，像是“最前沿的探索者”和“务实的实用主义者”。
    - **vs ZeroClaw**：ZeroClaw 明显是 OpenClaw 的生态下游（从其命名和大量配置、架构问题相似性可推断），但在创新提案（如Goal模式、Teams集成）上更为大胆，充当了OpenClaw社区的“创新试验田”。

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求/表现 |
| :--- | :--- | :--- |
| **会话状态持久化/管理** | **OpenClaw**, **NanoBot**, **Hermes Agent**, **ZeroClaw** | 所有项目均出现会话丢失、状态重置、参数丢失、内存泄漏、无限增长等问题。这是当前最核心的通用痛点。 |
| **安全与权限控制** | **OpenClaw**, **NanoBot**, **Hermes Agent**, **ZeroClaw** | 包含API Key明文存储、子代理权限绕过（严重）、Shell执行注入、敏感路径泄露等。安全已成为制约规模化部署的头号问题。 |
| **外部平台/通道集成** | **OpenClaw**, **NanoBot**, **Hermes Agent**, **ZeroClaw** | 社区对连接微信、iMessage、WhatsApp、Teams、语音服务等渠道的需求旺盛，希望Agent能成为沟通枢纽。 |
| **本地模型与性能优化** | **NanoBot**, **ZeroClaw** | 用户对Ollama缓存、内存溢出RSS增长等问题高度敏感，反映出本地部署对**资源效率和推理成本**的极致要求。 |

## 5. 差异化定位分析

- **功能侧重：**
    - **OpenClaw**: 全功能平台，强调**插件生态**与**架构纯净性**，社区更多为开发者/贡献者，讨论深度大。
    - **NanoBot**: 定位为**个人AI助手**，更关注日常使用的**易用性**和**安全性**，社区反馈偏向于具体使用中的 Bug 和功能（如WebUI、语音转录）。
    - **Hermes Agent**: **桌面客户端为先**，侧重于**交互体验**和**模型集成**（内置Mistral AI），其社区反馈集中于 UI/UX 问题和远程化需求。
    - **ZeroClaw**: 定位为**探索型智能体**，社区驱动了许多前沿特性（如Goal模式、多Agent协同、实时语音），显得更“极客”和实验性。
- **目标用户：**
    - **OpenClaw**: 开发者、深度用户、系统集成者。
    - **NanoBot**: 个人效率用户、本地模型爱好者。
    - **Hermes Agent**: 重度桌面用户、应用设计师。
    - **ZeroClaw**: 创新爱好者、高级玩家、研究型用户。
- **技术架构：**
    - **OpenClaw**: **插件式架构**，强调核心的轻量与插件的可扩展。
    - **NanoBot**: **会话式架构**，侧重于渠道（语音、WebUI、技能）的互联。
    - **Hermes Agent**: **桌面应用架构**，模型、会话、网关深度绑定在桌面客户端。
    - **ZeroClaw**: **早期模块化**，通过 RFC 推进频道和工具的运行时插件化，显露出向OpenClaw靠拢的架构演进趋势。

## 6. 社区热度与成熟度

**第一梯队（快速迭代，社区活跃）：**
- **NanoBot** & **Hermes Agent**：PR合并率高，维护者响应快，社区反馈能迅速转化为代码。属于“发现问题-解决问题”的高效循环。

**第二梯队（质量巩固，架构演进）：**
- **OpenClaw**：社区热度极高，但更侧重于深度的架构问题、功能讨论和积压清理，效率有所放缓，处于“从广到精”的转型期。

**第三梯队（探索实验，社区参与度高）：**
- **ZeroClaw**：贡献者提交大量Issue和PR，但核心维护者响应不足，导致“输入多、输出少”。虽然创新活力充沛，但项目成熟度和稳定性有待提升。

## 7. 值得关注的趋势信号

1.  **“会话即状态”成为行业共识与核心矛盾**：所有项目都在会话持久化上栽了跟头。这意味着Agent系统的有状态性从“feature”变成了“requirement”。开发者需要将**会话状态管理**视为与数据一致性和事务同等重要的系统性问题，而非简单的“存一下”即可。
2.  **安全防线正在从“功能”变为“架构”**：简单的白名单已无法防范Shell注入或子代理绕过。社区开始呼吁**微隔离、权限路由、工作区绑定**等架构级的安全方案。未来，安全能力将成为AI智能体系统最具竞争力的差异点。
3.  **协作与多模态是明确的下一代方向**：从Goal模式、Mixture-of-Agents到语音/视频集成，社区已不再满足于单机单会话的Agent。**自主规划**（Goal Tracking）、**多Agent协作**（MoA）、**多模态交互**（Speech/Vision Channel）正从“构想”走向“原型”，开发者应提前布局相应的数据管道和工具链。
4.  **“中国”用户需求成为不可忽视的力量**：OpenClaw和ZeroClaw报告中都出现了针对中文用户的特定问题（如国产包`@qingchencloud/openclaw-zh`的依赖问题、Windows下GBK编码问题）。这表明生态正在**全球化与本地化**之间寻找平衡，对多语言、多平台的支持将成为刚需。
5.  **代码合并效率是项目健康的“血压计”**：ZeroClaw活跃但停滞的PR列表，是一个明确的**红色预警**。对于任何开源项目，维持健康的PR合并速度（至少每周一次）是保持社区活力的关键。贡献者在等待回复时会逐渐失去耐心和动力。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot 项目动态日报 (2026-07-21)

## 1. 今日速览

过去24小时内，NanoBot项目保持了极高的活跃度，共处理 **11个 Issue**（关闭8个）和 **39个 PR**（合并/关闭22个）。社区贡献者积极响应，安全与稳定性修复是今日主轴：多个P1优先级的Bug（如内存溢出、子进程孤儿化、API密钥明文存储）得到了妥善解决。同时，WebUI、技能系统、新生态集成（ModelScope、Codex Fast）等功能性推进也在同步进行。总体来看，项目正处于密集的“补强与优化”阶段，健康度良好，维护者和社区协作效率高。

## 2. 版本发布
**无。** 过去24小时内未发布新版本。

## 3. 项目进展

今日项目在**安全加固、性能优化、功能增强、渠道扩展**四个维度取得了显著进展：

**安全性与稳定性修复 (已合并/关闭)**
- **PR #5006** (feat(channels): add guarded tool gateway): 实现了带守卫的工具网关协议，允许渠道（如语音频道）代理执行工具，同时保留完整的工作空间和文件状态上下文。*关闭 Issue #4911.*
- **PR #5014** (fix(files): reject oversized reads before loading): 修复了`read_file`将整个文件加载至内存导致OOM的严重缺陷。*关闭 Issue #4785.*
- **PR #4562** (fix(security): validate each shell segment against exec.allowPatterns): 安全增强，避免通过`&&`拼接绕过shell执行指令白名单。
- **PR #4594** (fix(exec): extract absolute paths after equals sign in shell guard): 修复shell守卫对`--output=/etc/passwd`形式参数的路径检测漏洞。
- **PR #4788** (fix(runner): stop catching KeyboardInterrupt/SystemExit): 修复`_run_tool()`中误捕获`BaseException`的问题，确保关键中断信号不被吞没。*关闭 Issue #4788.*
- **PR #4989** (fix(transcription): resolve ${VAR} env refs): 修复语音转录API key/env变量的插值问题。

**功能增强 (已合并/关闭)**
- **PR #5019** (feat(providers): support Codex fast mode): 支持OpenAI Codex Fast模式（`service_tier: "priority"`）。
- **PR #5016** (fix(webui): prioritize skill names in autocomplete): WebUI技能自动补全优化，长名称换行显示。
- **PR #5015** (fix(webui): keep Markdown table diffs inline): 修复Markdown表格在diff视图中的布局冲突问题。

**新技术集成 (待合并)**
- **PR #4965** (Feat/modelscope provider support): 新增ModelScope作为内置模型提供商，支持Qwen、DeepSeek等国产开源模型。

**总结**：过去24小时，NanoBot在安全堡垒和核心功能两个层面均向前迈了一大步。多达 **7个 P1优先级** 的问题已被清除，代码库变得更健壮、更可靠。

## 4. 社区热点

今日讨论最活跃的议题主要围绕**性能问题（Ollama缓存）** 及**新功能设计（受控工具网关）** 展开。

1.  **#4867 [CLOSED] [enhancement] Preserve exact prompt prefix to enable caching in Ollama** (22条评论)
    - **链接**: HKUDS/nanobot Issue #4867
    - **诉求**: 用户反馈在使用Ollama本地模型时，每次交互会额外增加 **60秒** 延迟，原因是NanoBot修改了prompt前缀导致无法利用Ollama的kv-cache。这直接影响了在32GB VRAM环境下的可用性。
    - **分析**: 该议题不仅涉及性能优化，更触及了本地模型部署的核心体验。用户期望NanoBot能尊重原始prompt结构以启用缓存，这是对“推理效率”的强烈诉求。虽已关闭，但解决方案的设计值得长期关注。

2.  **#4911 [CLOSED] [enhancement] A guarded tool gateway seam for channels** (1条评论，1个👍)
    - **链接**: HKUDS/nanobot Issue #4911
    - **诉求**: 提出渠道（如语音频道）需要一个受控的工具网关，使得外部模型可以调用Agent的Tools（如`function_call`）。核心矛盾是：当前渠道只处理文本，无法直接访问工具能力。
    - **分析**: 这是一个设计层面的前瞻性需求，标志着社区对**多模态、实时交互渠道**的探索。今日已通过**PR #5006**快速解决，社区响应非常高效。

## 5. Bug 与稳定性

今日报告的Bug数量不多，但质量很高，且多数已得到快速修复：

| 严重度 | Bug描述 | Issue链接 | 状态 | 关联Fix PR |
| :--- | :--- | :--- | :--- | :--- |
| **P0-紧急** | `read_file`加载大文件导致OOM | [#4785](HKUDS/nanobot Issue #4785) | **已关闭** | #5014 |
| **P0-紧急** | 子进程在Gateway退出后成为孤儿 | [#4794](HKUDS/nanobot Issue #4794) | **已关闭** | (等待合并) |
| **P1-严重** | 工具执行误捕获`KeyboardInterrupt` | [#4788](HKUDS/nanobot Issue #4788) | **已关闭** | #4811 |
| **P1-严重** | `Session.messages`内存泄漏 (无界增长) | [#4787](HKUDS/nanobot Issue #4787) | **已关闭** | (含修复) |
| **P1-严重** | API密钥以明文存储于`config.json` | [#4803](HKUDS/nanobot Issue #4803) | **未关闭** | 暂无 |
| **P2-重要** | `<tool_call>` 函数导致网关无限循环 | [#4864](HKUDS/nanobot Issue #4864) | **未关闭** | 暂无 |

**特别关注**：**Issue #4803（API密钥明文存储）** 属于严重的安全漏洞，虽已提出14天但尚未有关联的Fix PR，安全审计需优先处理。

## 6. 功能请求与路线图信号

- **Shell执行前需用户确认 (Issue #5013)**: 用户提出在执行shell命令前增加人工确认机制以降低风险。此功能与已有的安全加固（如PR #4562、#4594）形成互补，**极有可能被纳入下一版本**的渠道或WebUI层。
- **Dokploy部署模板 (Issue #1503)**: 已开放长达4个月，用户请求官方模板以便非技术人员快速部署。虽然长期未被标记，但反映了对**低门槛部署体验**的持续期待。
- **技能系统显式上下文加载 (PR #5018)**: 该PR允许调用者主动加载指定技能，而不是仅依赖`always: true`自动加载。这是一个关键的**开发者体验改进**，预计将在技能生态扩展后成为标配。

## 7. 用户反馈摘要

- **正面反馈**: 社区对安全漏洞（如OOM、脚本注入）的快速响应表示认可。PR #5006（受控工具网关）的实现解决了语音频道等场景的功能痛点，获得了社区肯定。
- **负面/痛点**:
  - **Ollama性能问题**: 如前所述，用户因Ollama缓存失效导致60秒延迟而抱怨“完全无法使用”。这是**本地推理用户的核心痛点**。
  - **WebUI重启后会话丢失**: 用户发现使用WebUI时，不同会话的文件上下文会混淆，且在重启后作用域会回退到默认值（与PR #4941相关）。这表明会话持久化和恢复逻辑仍有待完善。

## 8. 待处理积压

以下为长期未响应或关键但暂无进展的Issues/PRs，建议维护者重点关注：

1.  **Issue #1503 [OPEN] Template for Dokploy (创建于2026-03-04)**
    - **链接**: HKUDS/nanobot Issue #1503
    - **状态**: 4个月未分配，暗示项目当前对一键部署模板的支持优先级较低。

2.  **Issue #4803 [OPEN] Security: API keys stored as plaintext (创建于2026-07-06)**
    - **链接**: HKUDS/nanobot Issue #4803
    - **状态**: 严重的**安全缺陷**，虽已有明确改建议（`exclude=True`），但至今无关联修复PR。建议立即排期。

3.  **Issue #4864 [OPEN] Endless loop for <tool_call> (创建于2026-07-09)**
    - **链接**: HKUDS/nanobot Issue #4864
    - **状态**: 一个可能导致网关无限循环的bug，目前无讨论进展，需立即排查。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的关于 Hermes Agent 的 GitHub 数据，为您生成 2026-07-21 的项目动态日报。

---

# Hermes Agent 项目动态日报 — 2026-07-21

**报告周期:** 2026-07-20 至 2026-07-21
**数据来源:** NousResearch/hermes-agent GitHub

---

### 1. 今日速览

今日 Hermes Agent 项目处于 **高度活跃** 状态。过去 24 小时内，项目更新了 100 条 Issue 和 PR，新发布了一个里程碑式的 **v0.19.0 “Quicksilver” 版本**。社区讨论热烈，主要围绕桌面客户端的各种 Bug（如会话状态异常、UI 和性能问题）以及插件、网关等核心功能的扩展与优化。同时，多个安全相关的 Bug 和 PR 被提出，显示项目在快速迭代的同时也在积极修复稳定性问题。项目整体向前迈出了一大步，但大量的反馈也表明，新版本在桌面端的稳定性和用户体验上仍存在挑战。

### 2. 版本发布

Hermes Agent 于昨日发布了 **v0.19.0 (v2026.7.20) “The Quicksilver Release”**。这是一个重大版本更新。

-   **更新内容:** 从 v0.18.0 版本以来，项目完成了约 2,245 次提交，合入了 1,065 个 PR，关闭了约 3,300 个 Issues。社区贡献者超过 450 人，代码变动涉及约 30 万行新增和 3.6 万行删除。本次发布代号“水银”，暗示其流动性和灵活性可能是本次更新的主题。
-   **破坏性变更:** 报告未明确指出破坏性变更。
-   **迁移注意事项:** 虽然无官方迁移指南，但考虑到发布的规模，建议用户关注 Release Notes 中的任何配置项变化。风险较高的区域包括**插件接口 (Plugin Interface)**、**网关 (Gateway)** 以及**桌面客户端 (Desktop)** 的会话管理与后台逻辑。
-   **链接:** [Hermes Agent v0.19.0 Release](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.20)

### 3. 项目进展

过去 24 小时内，有 4 个 PR 被合并或关闭，标志着以下重要进展：

-   **UI/UX 修复:** PR #68639 解决了桌面客户端 `⌘W` 快捷键在预览文件标签页状态不一致时无法正确关闭文件的问题，提升了 Mac 用户的体验。
    -   链接: [PR #68639](https://github.com/NousResearch/hermes-agent/pull/68639)
-   **代码美化与 CI:** PR #68675 是一次自动格式化操作，合并了由 `npm run fix` 产生的代码风格修复，确保代码库的整洁性。
    -   链接: [PR #68675](https://github.com/NousResearch/hermes-agent/pull/68675)
-   **功能实现:** Issue #68588 被关闭，意味着 **Mistral AI** 已作为可选择的**内置提供商**被集成，用户无需手动配置即可直接选择该模型。
    -   链接: [Issue #68588](https://github.com/NousResearch/hermes-agent/issues/68588)
-   **功能调整:** Issue #65905 被关闭，解决了持久化上下文窗口缓存可能因提供商模型目录变动而返回错误值的问题，增强了兼容性。
    -   链接: [Issue #65905](https://github.com/NousResearch/hermes-agent/issues/65905)

### 4. 社区热点

今日最受关注的 Issues 反映了社区对**桌面客户端稳定性**和**插件生态扩展**的强烈关注。

-   **#64182 - Plugin Interface Expansion (15条评论):** 该 Issue 作为跟踪贴，用于讨论和规划核心 Agent 的插件接口扩展。拥有 15 条评论，显示了社区对提升可扩展性和第三方集成的浓厚兴趣。
    -   链接: [Issue #64182](https://github.com/NousResearch/hermes-agent/issues/64182)
-   **#38602 - Desktop Client-Only Installation (13条评论，50 👍):** 该功能请求获得了 50 个赞和 13 条评论，热度极高。用户希望 Hermes Desktop 能作为一个“瘦客户端”连接到远程 Hermes 实例，而不是必须在本机运行时启动一个完整的 Agent 后端。这表明很多用户有远程部署或集中管理的需求。
    -   链接: [Issue #38602](https://github.com/NousResearch/hermes-agent/issues/38602)
-   **#63078 - Blank Session Bug (9条评论):** 这是一个严重的 Bug，用户在桌面端新建会话后发送第一条消息，会创建一个空白会话。9 条评论表明许多用户可能遇到了同样的问题，严重影响了使用初体验。
    -   链接: [Issue #63078](https://github.com/NousResearch/hermes-agent/issues/63078)

### 5. Bug 与稳定性

今日报告的 50 个 Issue 中，大部分为 Bug 报告。按严重程度排列如下：

-   **严重 (P2) / 阻塞性 (Blocker):**
    -   **#67762:** `agent.session_estimated_cost_usd` 在网关重启后重置为 0，导致账单显示不准，影响依赖此功能的所有场景。
        -   **状态:** 待解决
        -   链接: [Issue #67762](https://github.com/NousResearch/hermes-agent/issues/67762)
    -   **#68369:** `hermes skills check` 在中文 Windows 系统上因编码问题崩溃（GBK vs UTF-8）。
        -   **状态:** 待解决
        -   链接: [Issue #68369](https://github.com/NousResearch/hermes-agent/issues/68369)
-   **中等 (P2):**
    -   **#63078:** 新会话第一条消息导致空白会话（见“社区热点”）。
        -   **状态:** 待解决
        -   链接: [Issue #63078](https://github.com/NousResearch/hermes-agent/issues/63078)
    -   **#68563:** 网关持久化会话在 `SOUL.md` 变更后不刷新系统提示词。
        -   **状态:** 待解决
        -   链接: [Issue #68563](https://github.com/NousResearch/hermes-agent/issues/68563)
    -   **#67871:** 运行中的压缩桌面会话替换了完整的对话记录，导致消息丢失。
        -   **状态:** 待解决
        -   链接: [Issue #67871](https://github.com/NousResearch/hermes-agent/issues/67871)
    -   **#68531:** `BaseEnvironment.__del__` 在解释器关闭时运行清理同步操作，可能导致不可预知的后果。
        -   **状态:** 待解决
        -   链接: [Issue #68531](https://github.com/NousResearch/hermes-agent/issues/68531)
    -   **#68559:** 多路复用网关忽略路由配置的终端后端，导致 Docker 容器继承了错误的本地后端。
        -   **状态:** 待解决
        -   链接: [Issue #68559](https://github.com/NousResearch/hermes-agent/issues/68559)
-   **低优先级 (P3):**
    -   **#63047:** 桌面端发送约5条消息后无响应（macOS）。
    -   **#68461:** 底部菜单因会话计时器时间长度变化而抖动，影响视觉效果。
    -   **#68634:** 桌面端渲染重复的 “Summarizing thread” 计时器。

### 6. 功能请求与路线图信号

社区提出的新功能需求主要包括：

-   **客户端隔离性与远程化:** **#38602**（桌面端瘦客户端）需求极高，若实现将允许用户使用轻量级前端连接强大的远程后端。这与 PR #17938（网关工作区绑定）的思路一致，旨在增强安全隔离和部署灵活性。
-   **搜索能力:** **#68635** 请求为桌面客户端添加 `⌘F` 搜索聊天记录的功能。这是一个提升用户日常使用便利性的基础功能。
-   **生态系统扩展:**
    -   **#68618** 请求为 macOS 版本使用开发者 ID 签名，以解决 TCC 权限每次更新后都需要重新授权的问题，改善 Mac 用户体验。
    -   **#68679** 是一个开放的 PR，旨在为 OpenRouter 提供商添加策略感知模型目录和内容控制（ZDR）功能，响应了社区对更多模型提供商控制权的要求。
        -   **状态:** 待合并
        -   链接: [PR #68679](https://github.com/NousResearch/hermes-agent/pull/68679)

### 7. 用户反馈摘要

从今日的 Issues 和 PR 评论中，可以提炼出以下用户痛点和使用场景：

-   **桌面端新用户首次体验差:** Issue **#63078** (空白会话) 和 **#63047** (5条消息后无响应) 表明，新用户首次使用很可能会遭遇严重 Bug，导致无法正常开始使用。
-   **UI/UX 细节粗糙:** 用户 **@networthexplained** 报告的 **#68461** (菜单抖动) 和 **#68640** (启动时闪白屏) 指向了桌面客户端在 UI 细节打磨上的不足。这位用户也提出了“屏幕闪瞎我”这样生动的反馈。
-   **配置和集成痛点:**
    -   用户希望更简便地集成外部模型（**#68588** - Mistral AI 作为内置提供商）。
    -   用户对持久化配置的期待很高，如 **#68563** (SOUL.md 变更不生效) 反映了用户修改 Agent 人格设定后期望立即生效的心理。
-   **特定平台问题:** 多个 Bug 集中在 **Windows** 平台（**#68369**, **#68484**, **#68609**），表明 Windows 版本的兼容性和稳定性测试有待加强。
-   **Agent 行为不可预期:** **#68529** 描述 Agent 对 `~/` 路径解析不一致，有时指向 Docker 容器的挂载卷，有时指向家用目录。这种不明确的路径解析行为会严重影响 Agent 在自动化脚本中的可靠性。

### 8. 待处理积压

-   **高重要性长线 PR:**
    -   **#17938** (feat(gateway): guard repo side effects with workspace binding): 这是一个已存在近3个月的 PR，旨在增强网关的安全性，防止会话影响外部仓库。考虑到其广度 (`blast: broad`) 和安全性 (`type/security`)，应优先推动审查和合并。
        -   链接: [PR #17938](https://github.com/NousResearch/hermes-agent/pull/17938)
    -   **#65260** (fix: bound Hermes session state growth safely): 一个已存在6天的 PR，旨在限制会话状态数据库的无限制增长，这对于大型生产部署至关重要。它被标记为影响广泛，值得关注。
        -   链接: [PR #65260](https://github.com/NousResearch/hermes-agent/pull/65260)
-   **被用户高频顶起的 Issue:**
    -   **#38602** (Desktop Client-Only Installation): 如前所述，这是社区高度期待的功能需求，应被视为未来的路线图重点。
        -   链接: [Issue #38602](https://github.com/NousResearch/hermes-agent/issues/38602)
-   **复杂的老 Bug:**
    -   **#39497** (多人报告多种Bug): 该 Issue 自6月以来未结案，由 Agent 自身报告的复杂 Bug 组合，涉及配置、命令和应用挂起。虽然被标记为低优先级 (P3)，但 Agent “自报Bug”的情况需引起关注。
        -   链接: [Issue #39497](https://github.com/NousResearch/hermes-agent/issues/39497)

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 ZeroClaw 项目的 AI 智能体与个人 AI 助手领域开源项目分析师，我已根据您提供的数据，为您生成了 2026-07-21 的 ZeroClaw 项目动态日报。

---

## ZeroClaw 项目动态日报 | 2026-07-21

### 1. 今日速览

今日 ZeroClaw 项目处于 **高活跃度** 状态，社区提交和讨论热情高涨。过去24小时内，项目共产生 100 条 Issues 和 PRs 更新，但 **零合并/关闭**，反映出项目当前主要处于新功能设计和问题反馈的“输入”阶段，而代码层面的“消化”与“输出”速度有所滞后。值得注意的是，P1 优先级（严重）的 Bug 报告激增，尤其在配置管理和安全方面，但多个关键问题已有相应的修复 PR 在等待合并，项目整体稳定性正面临考验。同时，社区驱动的功能增强提案（如 Teams 频道支持）和架构重构（RFC）讨论活跃，为项目发展提供了清晰的方向。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日项目在代码合并方面进展有限，过去24小时内仅有 **3 个 PR 被合并/关闭**，未落入“最新 PR”列表的前20条，表明核心代码变更相对停滞。社区贡献者提交了大量待审查的 PR（47个），主要聚焦于修复已知的高风险 Bug，是整个项目修复存量问题、提升稳定性的关键。这些待合并的 PR 覆盖了以下几个核心方向：

- **安全与稳定性修复**：多个针对 MCP 服务器僵尸进程、Landlock 沙箱逃逸、Channel 监听器错误重启等问题的高风险修复 PR 正在等待审核。这表明社区正在积极应对项目当前最突出的稳定性挑战。
- **新功能集成**：一个重要的 **Microsoft Teams 频道**支持 PR (#9241) 已提交，标志着 ZeroClaw 在连接外部平台方面迈出新的一步。
- **架构优化**：关于“将频道与工具从编译时特性迁移到运行时插件”的 RFC (#8850) 和“OpenAI Chat Completions 兼容适配器”的 RFC (#8603) 均进入开发阶段，体现了项目向更模块化、更易集成方向演进的趋势。

### 4. 社区热点

以下 Issues 和 PR 是今日社区讨论的焦点，反映了用户最关心的问题和方向：

- **[Feature]: Add typed per-agent git identity (#8226)**：评论数最多（6条）。用户希望为内置的 Git 操作增加为每个代理独立配置身份的功能。这反映了在复杂工作流或团队协作场景下，对细粒度身份管理的需求，尤其是在多租户架构下。
- **[Bug]: Telegram channel cannot be configured (#8505)**：评论数最多（6条）。这是一个严重的配置问题，用户报告按照快速入门指南也无法正确配置 Telegram 频道。该 Issue 暴露了配置流程或文档的短板，是影响新用户上手体验的关键痛点。
- **[[Bug]: delegate bypasses parent's tool allowlist (#8279)**：安全风险极高（S0级）。用户发现 `delegate` (代理) 工具可以绕过父代理的工具白名单，这是一个严重的权限提升漏洞，直接威胁系统安全。
- **[Bug]: MCP/tool-schema cloning drives unbounded RSS growth (#8642)**：被列为 P1 优先级的性能 Bug，描述了 MCP 工具模式克隆导致 Agent 循环中 RSS 内存无限制增长的问题，是导致用户 OOM（内存溢出）的根本原因之一。
- **PR #9241: feat(channels): add Microsoft Teams (Bot Framework) channel**：作为最新提交的 PR，它代表了社区对拓展 ZeroClaw 应用场景的迫切期望，将 Agent 的能力带入企业级协作平台。

### 5. Bug 与稳定性

今日报告的 Bug 主要集中在 **配置管理、安全、性能和渠道** 四大领域。以下是按严重性排列的突出问题：

- **S0 - 数据丢失/安全风险：**
    - `[Bug]: delegate bypasses parent's tool allowlist` (#8279)：子代理可执行父代理禁止的工具，严重安全漏洞。**尚无关联修复 PR。**
- **S1 - 工作流受阻：**
    - `[Bug]: Telegram channel cannot be configured` (#8505)：基本配置失效，影响新用户接入。**尚无关联修复 PR。**
- **S2 - 功能降级：**
    - `[Bug]: MCP/tool-schema cloning drives unbounded RSS growth` (#8642)：Agent 循环中内存无限增长，导致 OOM。**尚无关联修复 PR。**
    - `[Bug]: Stdio-based MCP servers accumulating as zombie processes` (#8731)：MCP 服务器进程无法被正确回收，变成僵尸进程，消耗系统资源。**已有高优先级修复 PR #8948。**
    - `[Bug]: zeroclaw config init ships a config template that its own daemon rejects` (#8718)：初始配置模板无法被守护进程正确解析，导致功能静默失效。**尚无关联修复 PR。**
    - `[Bug]: compatible provider silently deletes content via unconditional <think> tag stripping` (#8615)：内容被静默删除，虽然无数据丢失风险，但用户体验极差。**尚无关联修复 PR。**
- **配置相关（P2/P3）：**
    - 一系列由 `yanchenko` 提交的配置 Bug（#9236, #9237, #9238, #9239, #9240），深入描述了 `config set`、`save_dirty` 等功能的底层问题，包括路径解析错误、Windows 兼容性问题和回滚逻辑缺失，表明项目的配置子系统存在系统性缺陷。

### 6. 功能请求与路线图信号

未来的功能发展重点清晰，主要围绕 **架构现代化、生态兼容性和用户体验优化**：

- **近期可实现（已有对应 PR 或深入讨论）：**
    - **Microsoft Teams 频道**：PR #9241 的提交表明该功能已进入开发阶段，预计很快会被纳入主线。
    - **PowerShell 原生支持**：PR #9182 旨在解决 Windows 平台下 `runtime.shell` 配置被忽略的问题，这将显著提升 Windows 用户的使用体验。
    - **OpenAI Chat Completions 兼容**：RFC #8603 进入开发阶段 (`status:in-progress`)，这将使 Open WebUI 等客户端可直接连接 ZeroClaw，极大扩展其生态。
    - **运行时插件化**：RFC #8850 (`status:in-progress`) 描述的战略目标，将彻底改变项目扩展方式，降低使用门槛，增强二进制文件的可移植性。
- **长期规划（RFC 或讨论阶段）：**
    - **Goal 模式**：RFC #8303 提出了一种全新的“目标导向”会话模式，让 Agent 可以自主完成复杂任务，这将是项目能力的重大飞跃。
    - **实时语音通道**：RFC #8780 规划了通过 Gemini Live 等后端实现实时语音交互的功能，将 ZeroClaw 推向多模态交互的前沿。
    - **Mixture-of-Agents (MoA)**：Issue #8568 提出的 MoA 虚拟模型提供者，旨在聚合多个模型能力解决复杂问题，是 Agent 协作的高级形态。

### 7. 用户反馈摘要

从 Issues 的评论中可以提炼出以下真实的用户声音：

- **上手体验的挫折感**：配置问题（如 #8505, #8718）让新用户感到困惑和沮丧。“silently broken”（静默破坏）是高频出现的关键词，用户对错误不报、配置无效没有提示的情况非常不满。
- **对安全与透明性的期望**：用户对 `delegate` 的权限绕过漏洞（#8279）表现出了高度警觉，并希望通过“有意的无回复”机制（#8410）来让 Agent 的行为更加透明和可控。这表明用户不仅是使用工具，更在关注 Agent 的行为安全与可预测性。
- **对平台扩展的渴望**：从 Teams 频道（#9241）和 Speech-to-Speech 通道（#8780）的需求来看，用户希望 ZeroClaw 能成为连接各类工作平台和交互方式的枢纽。
- **对文档质量的不满**：用户 `cr3a7ure` 在 Bug #8810 中用“slop remains slop”（如果实现不正确，文档乱写依然是乱写）来尖锐地批评文档错误问题，显示出一部分专业用户对项目初期的粗糙之处直言不讳。同时，对缺失的 SOP 语法示例（#8587）和 Bedrock 配置说明（#8925）的需求也十分迫切。

### 8. 待处理积压

以下 Issue 和 PR 长期未被响应或合并，可能成为项目的技术债务或潜在风险：

- **[RFC]: Goal mode for bounded autonomous session work (#8303)**：自 6月24日创建，评论4条，获得1个 👍。这是一个具有里程碑意义的功能设计，但至今仍无明确的时间表或 assignee，可能导致社区热情消退。
- **[Bug]: delegate bypasses parent's tool allowlist (#8279)**：作为 S0 级别安全漏洞，至今无修复 PR，也未被分配责任人。这类问题若持续存在，将对项目声誉造成严重打击。
- **大量标记为 `needs-author-action` 的 PR（如 #8438, #8781, #8948, #9075 等）**：这些 PR 贡献者可能因未收到维护者的及时反馈或因某些原因未能跟进修改，长期处于悬停状态。这不仅浪费了社区贡献者的精力，也阻塞了 Bug 修复和新功能的合入。

</details>

---
*本日报由 [agents-radar](https://github.com/7ky-bk/agents-radar) 自动生成。*