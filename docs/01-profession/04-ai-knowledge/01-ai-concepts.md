## LLM
Large Language Model
底层引擎：transformer架构

### Transformer 架构简介
Transformer 是 2017 年由 Google 在论文《Attention Is All You Need》中提出的深度学习架构，完全基于自注意力机制（Self-Attention），摒弃了传统的循环神经网络（RNN）和卷积神经网络（CNN）结构。其核心组成包括：编码器（Encoder）和解码器（Decoder）堆叠的多层结构、多头注意力机制（Multi-Head Attention）、前馈神经网络（Feed-Forward Network）以及残差连接和层归一化。Transformer 的优势在于能够高效地并行处理序列数据，捕捉长距离依赖关系，已成为当今大语言模型（如 GPT、BERT、LLaMA 等）的基础架构。

### 国内外头部大模型对比（截至 2026 年 7 月）

#### 国外大模型

| 公司 | 模型名称 | 最新版本 | 优势 | 劣势 |
|------|----------|----------|------|------|
| OpenAI | GPT | GPT-5.5 / GPT-4o | 生态最完善，工具链丰富，推理与代码能力均衡，Terminal-Bench 达 82.7% | API 价格较高，闭源不可自部署，国内访问受限 |
| Anthropic | Claude | Claude Opus 4.7 | 编程能力顶尖，SWE-bench 达 80.9%，创意写作与学术论文理解能力强 | 多模态能力相对弱，API 价格偏高 |
| Google | Gemini | Gemini 3 / 2.5 Pro | 多模态能力最强，原生超长上下文（百万级 token），性价比高 | 中文理解不如国产模型，部分场景需多次追问 |
| Meta | Llama | Llama 4（405B/70B/8B） | 开源免费，可本地部署，社区生态庞大，8B 版可在手机端运行 | 性能略逊于顶级闭源模型，上下文长度有限 |
| xAI | Grok | Grok 系列 | 与 X（Twitter）实时数据深度集成，风格自由 | 通用能力不及第一梯队，生态尚不成熟 |

#### 国内大模型

| 公司 | 模型名称 | 最新版本 | 优势 | 劣势 |
|------|----------|----------|------|------|
| 深度求索 | DeepSeek | DeepSeek-R1 / V3（685B） | 推理能力极强（R1 专精思维链），API 价格极低（约为 GPT 的 1/10），开源 | 多模态能力较弱，品牌生态不如大厂完善 |
| 阿里巴巴 | 通义千问 Qwen | Qwen 3 系列 | 开源生态好，企业级应用成熟，多尺寸模型覆盖端到云 | 旗舰模型绝对性能略逊 GPT/Claude |
| 百度 | 文心一言 ERNIE | ERNIE 4.0+ | 中文理解深厚，搜索生态整合，政企客户基础广 | 开源程度低，开发者社区活跃度一般 |
| 字节跳动 | 豆包 Doubao | Doubao 系列 | 依托字节流量入口，C 端用户量大，多模态能力不断提升 | 开发者生态起步较晚，API 开放度有限 |
| 智谱 AI | ChatGLM / GLM | GLM-5 | 学术背景强，开源模型口碑好，企业服务完善 | 品牌影响力与资金规模不及大厂 |
| 月之暗面 | Kimi | Kimi K3（开源 2.8 万亿参数） | 超长上下文处理能力突出，首个开源万亿级模型 | 多模态能力有限，商业化仍在探索 |

### 编码与解码
Tokenizer
大模型只使用数字矩阵，用户的输入（文本内容）需要经过编码转换为数字序列（token）。
编码分两步：第一步，切分为片段（token）；第二步，将每个片段映射为数字（Token ID）。两者具有唯一对应关系。
解码只有一个步骤：将数字序列转换为文本内容。
Token是大模型处理的基本单位，每个Token对应一个字符或单词。

### 上下文
context，大模型每次处理任务时接收到的信息总和。可理解为大模型的临时记忆体。
最基础的做法：每次处理任务时将历史对话内容重新发送给大模型，使大模型看上去有记忆，能够回答之前相关的问题。
context中包含的内容：对话历史、用户问题、当前输出、工具
上下文窗口，context window：context能容纳的最大token数量。目前主流约100万左右（1个Token约1.5个汉字，可容纳150万个汉字）。

### RAG
场景：当需要额外提供特有资料，如公司的产品手册、法律文件等。把所有外部文件加载到context中既不方便又成本高昂，引入了RAG（Retrieval-Augmented Generation）技术解决该问题。
RAG技术的基本原理是：将用户的问题和上下文中的信息进行匹配，找到最相关的资料，然后将这些资料作为上下文的一部分，发送给大模型进行处理。

### Prompt
提示词，给大模型的问题或指令。
System Prompt：大模型的初始指令，用于引导大模型的行为。
User Prompt：用户的问题或指令。说明具体的任务。
Tool Prompt：大模型调用工具时的指令。
好的prompt应该是清晰的、具体的、明确的。Prompt会决定生成的结果质量。Prompt Engineering, 本质上是如何把话说清楚，让大模型的结果质量更高。因其门槛低、大模型能力越来越强不需要提示词太清楚，因此重要性下降了。

### Tool
工具，大模型可以调用的外部程序或服务。
大模型需要借助平台的能力才能调用工具。平台串联工作流程。

### Agent MCP   
一开始各家平台（Anthropics、OpenAI等）有自己的工具接入标准。
Model Context Protocol，模型上下文协议。统一的工具接入标准。

### Agent
智能体, 能够自主规划、自主调用工具直至完成用户任务的系统。

Agent Runtime（Tool章节中平台的作用）
LLM只是文本生成器。执行能力需要Agent Runtime/Agent Framework完成。
常见的Runtime有，LangChain, AutoGPT, OpenAI Function Calling, Trae的tool系统。
具备的能力：解析LLM的tool调用指令，路由到对应的tool并执行，处理结果并返回未LLM。

### Agent Skill
提前写好，塞给Agent的说明文档。
适合固定流程的，SOP（Standard Operating Procedure，标准操作程序）等
#### 格式
```markdown
---
name: go-out-checklist
description:
---
指令内容，没有强制标准
```
#### 路径
以Claude Code为例，用户主目录/.claude/skills/<go-out-checklist>/SKILL.md


### Loop Engineering
