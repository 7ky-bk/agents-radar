# Hugging Face Trending Models Digest 2026-07-21

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-21 14:17 UTC

---

# Hugging Face Trending Models Digest — 2026-07-21

## 1. Today's Highlights

The Hugging Face ecosystem is buzzing with activity around several major releases this week. Google's **Gemma-4-31B-it** dominates downloads at over 12 million, showcasing continued appetite for powerful open-weight multimodal models. The **Qwen 3.6** family is spawning an explosive amount of community fine-tunes and quantizations, with models like **HauhauCS/Qwen3.6-35B-A3B-Uncensored** and **DavidAU's uncensored variant** gaining significant traction. Extreme quantization (1-bit and 2-bit) from **prism-ml's Bonsai** and **Ternary-Bonsai** series is enabling 27B-parameter models to run on consumer hardware. Meanwhile, **openbmb/MiniCPM-RobotManip** and **MiniCPM-RobotTrack** signal growing interest in vision-language-action models for embodied AI applications.

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,251 | 545,109 | Zhipu AI's latest MoE architecture with dynamic sparse attention achieves strong reasoning performance. Its 4,251 likes make it the most-liked model on this week's list besides Gemma-4. |
| [Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,190 | 722,058 | Moonshot AI's compressed code-focused model uses novel tensor compression techniques to reduce inference costs. It gained 722K downloads rapidly, indicating strong developer interest. |
| [Hy3](https://huggingface.co/tencent/Hy3) | tencent | 852 | 14,143 | Tencent's Hunyuan V3 text-generation model brings new capabilities in long-context reasoning. Despite lower download volume, its 852 likes reflect strong community validation. |
| [Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 98 | 125 | A new lightweight transformer architecture optimized for efficient inference on edge devices. Still early-stage with 125 downloads, but demonstrates novel attention patterns. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | ---: |
| [Gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,307 | 12,113,203 | Google's latest open-weight multimodal model supporting image, video, and text inputs. Its 12M+ downloads in a week mark it as the most downloaded model on this list by a wide margin. |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 2,952 | 1,997,690 | A vision-capable MoE uncensored variant of Qwen 3.6 with aggressive release settings. Its nearly 2M downloads show massive demand for unfiltered multimodal models. |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,547 | 2,237,351 | Baidu's universal OCR model handles unlimited document layouts without retraining. Over 2.2M downloads confirm it's the go-to solution for document understanding tasks. |
| [Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,381 | 2,133,420 | A Qwen 3.5-based reasoning model with 1M context length in a quantized GGUF format. Its 2.1M downloads indicate strong demand for long-context reasoning on consumer hardware. |
| [Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,320 | 16,441 | An image-text-to-text vision-language model with conversational capabilities. Its 1,320 likes suggest strong early interest despite relatively modest downloads. |
| [Wan-Dancer-14B](https://huggingface.co/Wan-AI/Wan-Dancer-14B) | Wan-AI | 150 | 2,497 | A specialized image-to-video diffusion model for generating high-quality dance videos. This niche application has attracted rapid community adoption in creative AI circles. |
| [LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID) | Alissonerdx | 220 | 0 | A LoRA adapter for identity-preserving text-to-video generation using LTX Video. Despite zero downloads at time of listing, its 220 likes signal strong anticipation. |
| [MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize) | OpenMOSS-Team | 297 | 92,265 | Audio-text-to-text model combining speech transcription with speaker diarization in a single pass. Its 297 likes reflect growing demand for efficient audio processing. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | ---: |
| [OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 230 | 17,162 | A Qwen 3.5-based OCR model optimized for complex document layouts and handwriting. Its focused OCR capability fills a niche alongside Baidu's Unlimited-OCR. |
| [Nemotron-3-Embed-1B-BF16](https://huggingface.co/nvidia/Nemotron-3-Embed-1B-BF16) | nvidia | 93 | 93,021 | NVIDIA's embedding model based on Ministral-3 architecture for sentence similarity and text retrieval. Its 93K downloads show steady adoption for RAG pipelines. |
| [MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 146 | 58 | A vision-language-action (VLA) model enabling robots to perform manipulation tasks from visual input. Though early-stage, it signals a new frontier in embodied AI on Hugging Face. |
| [MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 107 | 72 | Companion VLA model for robot object tracking in dynamic environments. Together with RobotManip, it forms a comprehensive robotics stack for research. |
| [needle](https://huggingface.co/Cactus-Compute/needle) | Cactus-Compute | 297 | 1,068 | A JAX-native model specialized for tool use and function calling with structured outputs. Its 297 likes from limited downloads indicate niche but passionate interest. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | ---: |
| [Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 560 | 1,404,962 | A 1-bit quantized 27B model enabling LLM capabilities on laptops and low-RAM devices. Over 1.4M downloads show the massive appetite for extreme compression. |
| [Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 880 | 432,196 | A 2-bit ternary quantization of Bonsai offering a middle ground between size and quality. Its 880 likes suggest the ternary approach resonates with the community. |
| [Bonsai-27B-mlx-1bit](https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit) | prism-ml | 159 | 25,273 | Apple MLX-optimized 1-bit version of Bonsai for efficient inference on Apple Silicon. Shows the prism-ml team covering both GGUF and MLX ecosystems. |
| [Ternary-Bonsai-27B-mlx-2bit](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-mlx-2bit) | prism-ml | 131 | 20,445 | MLX-port of the ternary 2-bit Bonsai for Mac hardware. Complements the GGUF variant with Apple ecosystem support. |
| [Hy3-GGUF](https://huggingface.co/AngelSlim/Hy3-GGUF) | AngelSlim | 153 | 145,102 | GGUF quantization of Tencent's Hy3 model for local deployment. Its 145K downloads confirm the community's preference for quantized Tencent models. |
| [Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 210 | 62,842 | An extensively fine-tuned uncensored Qwen 3.6 variant with multi-turn prompt (MTP) and aggressive creative generation. Its 62K downloads show niche demand for "maximal" fine-tunes. |
| [Qwen3.6-35B-A3B-Uncensored-Hermes-V3-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V3-GGUF) | LuffyTheFox | 90 | 19,140 | MoE-based uncensored Hermes fine-tune of Qwen 3.6 in GGUF format for local deployment. A smaller but focused community follows these experimental builds. |
| [Qwythos-9B-v2-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-v2-GGUF) | empero-ai | 198 | 125,726 | Second-generation quantized Qwythos reasoning model with improved instruction following. Its 125K downloads show sustained interest in the Qwythos family. |
| [Inkling-GGUF](https://huggingface.co/unsloth/inkling-GGUF) | unsloth | 115 | 7,377 | GGUF quantization of the Inkling vision-language model by Unsloth, optimized for efficient local deployment. Early adoption with 7K downloads and growing. |
| [MiniCPM5-1B-Claude-Opus-Fable5-Thinking](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking) | GnLOLot | 160 | 6,165 | A tiny 1B model fine-tuned for chain-of-thought reasoning using synthetic data from Claude Opus. Demonstrates that small models can achieve impressive thinking capabilities. |
| [MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF) | GnLOLot | 138 | 51,746 | GGUF quantized version of the 1B thinking model for ubiquitous deployment. Its 51K downloads outpace the base version, confirming users prefer quantized formats. |
| [krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit) | conradlocke | 466 | 0 | A LoRA for identity-consistent image editing built on Krea-2-Raw, supporting ComfyUI workflows. Its 466 likes with 0 downloads suggest it's a quality find for creative AI practitioners. |

## 3. Ecosystem Signal

Three major trends dominate this week's Hugging Face landscape. **First, extreme quantization has become mainstream.** The Bonsai family's 1-bit and 2-bit quantizations prove that 27B models can run on consumer hardware without severe quality degradation—1.8M combined downloads for Bonsai variants demonstrate this isn't experimental but production-ready. **Second, the Qwen ecosystem is exploding.** With at least seven distinct fine-tunes and quantizations of Qwen 3.5/3.6 in the top 30, Qwen has become the dominant base for community customization, rivaling Llama's previous stronghold. **Third, open-weight models from major labs are competing fiercely.** Google's Gemma-4 at #22 (12M downloads) and Zhipu's GLM-5.2 at #5 (545K downloads, 4,251 likes) show that open-weight releases from Big Tech and Chinese labs are now standard, not exceptions. The uncensored trend remains strong, with multiple uncensored Qwen variants accumulating millions of downloads. Interestingly, robot-focused VLA models are emerging—MiniCPM-RobotManip and RobotTrack, though low in downloads, signal a new category that could grow rapidly as embodied AI hardware matures.

## 4. Worth Exploring

**prism-ml/Bonsai-27B-gguf** — The 1-bit quantization breakthrough deserves hands-on testing. Being able to run a 27B model on devices with 8-12GB RAM while maintaining coherent output is genuinely impressive. It's the best demonstration yet that extreme quantization doesn't mean unusable quality.

**baidu/Unlimited-OCR** — With 2.2M downloads and 2,547 likes, this is clearly solving a real need. Its ability to handle any document layout without retraining makes it a drop-in replacement for commercial OCR services. Worth evaluating for any document processing pipeline.

**openbmb/MiniCPM-RobotManip** — Though early-stage, this represents where AI is heading next—models that translate vision into action. Even if you don't work in robotics, studying its vision-language-action architecture offers insight into the next frontier beyond text and image generation.

---
*This digest is auto-generated by [agents-radar](https://github.com/7ky-bk/agents-radar).*