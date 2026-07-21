# Hugging Face 热门模型日报 2026-07-21

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-21 14:17 UTC

---

好的，作为AI模型生态分析师，以下是基于您提供的数据生成的《Hugging Face 热门模型日报》。

---

### 每日模型日报 | 2026年7月21日

#### 📈 今日速览

本周Hugging Face生态呈现三大趋势：**多模态模型**与**超低比特量化**成为社区焦点。`google/gemma-4-31B-it`以超1200万下载量领跑，证明大厂开源模型依然拥有巨大流量。`zai-org/GLM-5.2`凭借超高周点赞数，显示国产MoE模型的巨大潜力。在量化领域，`prism-ml`团队推出的1-bit和Ternary（三值）Bonsai模型系列引发社区热议，标志着极致模型压缩技术的成熟。此外，社区涌现大量基于`Qwen3.6`的微调与量化版本，形成了繁荣的二次开发生态。

#### 🔥 热门模型

##### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,251 | 545,109 | 国产顶尖MoE模型，周点赞数最高，具备强大的对话和文本生成能力，社区关注度极高。 |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,307 | 12,113,203 | 谷歌最新开源大模型，下载量断层领先，支持图像和文本多模态输入，是当前最受欢迎的基础模型之一。 |
| [tencent/Hy3](https://huggingface.co/tencent/Hy3) | tencent | 852 | 14,143 | 腾讯最新发布的Hunyuan系列文本生成模型，点赞数高，预示着腾讯在开源大模型领域的持续发力。 |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 98 | 125 | 新晋专业领域模型，专注于特定特征提取，值得关注其下游应用潜力。 |

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,547 | 2,237,351 | 百度出品的高性能OCR模型，下载量和点赞数双高，在图像文本提取任务上表现出色，实用性极强。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,381 | 2,133,420 | 基于Qwen3.5的量化版推理模型，下载量巨大，表明社区对可用于本地部署的高效推理模型需求旺盛。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 2,952 | 1,997,690 | 社区魔改的Qwen3.6 MoE模型，采用“无审查”风格，点赞极高，体现了社区对模型个性化和开放性的追求。 |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,190 | 722,058 | 月之暗面推出的代码专用多模态模型，专为编程场景优化，显示了垂直领域模型的竞争力。 |
| [Wan-AI/Wan-Dancer-14B](https://huggingface.co/Wan-AI/Wan-Dancer-14B) | Wan-AI | 150 | 2,497 | 专业的图生视频模型，专注于舞蹈动作生成，是AIGC在视频内容创作领域的细分探索。 |
| [Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID) | Alissonerdx | 220 | 0 | 用于视频生成的身份保持LoRA，专注于视频中人物面部的一致性，是社区在视频编辑领域的创新尝试。 |

##### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 146 | 58 | 专注于机器人操作任务的VLA（视觉-语言-动作）模型，代表AI从理解世界到操作世界的趋势。 |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 107 | 72 | MiniCPM系列的机器人跟踪模型，同样属于VLA类别，显示了该团队在具身智能领域的布局。 |
| [nvidia/Nemotron-3-Embed-1B-BF16](https://huggingface.co/nvidia/Nemotron-3-Embed-1B-BF16) | nvidia | 93 | 93,021 | 英伟达推出的小型但高效的句子嵌入模型，广泛应用于RAG和语义搜索，下载量可观。 |
| [Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle) | Cactus-Compute | 297 | 1,068 | 基于JAX的轻量级模型，专注于函数调用和工具使用，代表了AI agent能力的重要方向。 |

##### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 880 | 432,196 | **三值量化**的Bonsai模型，将模型精度压缩至2-bit，是前沿量化技术的代表，显著降低部署门槛。 |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 560 | 1,404,962 | **1-bit**量化的Bonsai模型，下载量巨大，证明了极端量化在社区中的高需求和接受度。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 210 | 62,842 | 社区深度微调与量化的Qwen3.6变体，名称极具风格，反映了社区创作的自由度和丰富性。 |
| [AngelSlim/Hy3-GGUF](https://huggingface.co/AngelSlim/Hy3-GGUF) | AngelSlim | 153 | 145,102 | 腾讯Hy3模型的社区量化版，下载量高，表明社区对高质量基础模型的量化版本有急切需求。 |
| [empero-ai/Qwythos-9B-v2-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-v2-GGUF) | empero-ai | 198 | 125,726 | Qwythos系列模型的第二代量化版，维持了高热度，证明该系列模型的持续受欢迎。 |

#### 🌍 生态信号

1.  **Qwen家族与MoE架构成主流**：本周榜单中，Qwen3.5/3.6系列及其衍生模型占据了半壁江山，已成为社区进行二次开发和量化的首选基座。同时，`GLM-5.2`等MoE架构模型的高点赞率，说明社区对稀疏激活、高效推理的模型架构热情高涨。
2.  **极致量化技术破圈**：`prism-ml`的Bonsai系列（1-bit & Ternary）不仅技术上亮眼，更在社区获得大量应用（GGUF版总下载超180万）。这表明行业正从“追求更大模型”转向“在终端部署极致压缩模型”，量化技术进入“bit级”竞争时代。
3.  **多模态与具身智能萌芽**：虽然传统LLM仍是主流，但多模态（图像、视频、音频）模型已成为新模型的标配。特别是`openbmb`的MiniCPM-Robot系列，虽然下载量尚小，但代表了从“感知理解”向“物理交互”进军的明确信号，是值得长期关注的AI方向。

#### 🔭 值得探索

1.  **[google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it)**：作为下载量王者，它是评估当前大模型技术与社区热度的最佳基准。其强大的多模态能力值得所有开发者体验和研究。
2.  **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**：1-bit量化的巅峰之作。如果你对模型压缩和边缘端部署感兴趣，这个模型是绝佳的研究样本，其性能与体积的平衡令人惊叹。
3.  **[openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip)**：想要窥见AI的未来，可以尝试这个模型。它是少有且开源的VLA模型，代表了AI从纯粹的数字世界迈向物理世界的关键一步，是研究与实验的前沿阵地。

---
*本日报由 [agents-radar](https://github.com/7ky-bk/agents-radar) 自动生成。*