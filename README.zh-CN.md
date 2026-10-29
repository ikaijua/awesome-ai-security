# Awesome AI Security

[English](README.md) | **简体中文**

**发现 AI 安全领域值得使用的工具、值得关注的人与团队，以及值得投入的前沿方向。**

A curated map of AI security tools, people, teams, and research frontiers.

面向安全工程师、研究者和 AI 应用开发者的资源导航。重点关注 LLM、Agent 和 AI 应用安全，同时覆盖模型与数据安全，以及 AI 在网络安全中的应用。

[工具](#tools) · [人物](#people) · [团队与社区](#teams) · [前沿方向](#frontiers) · [动态与讨论](#discussions) · [参与贡献](CONTRIBUTING.zh-CN.md)

## 如何使用

| 你想做什么 | 从这里开始 |
| --- | --- |
| 为 AI 应用选择评测与防护工具 | [工具](#tools)：按场景查找，结合使用边界判断 |
| 跟进研究者的持续输出 | [人物](#people)：从 X 账号、博客与代表成果进入 |
| 寻找研究团队、开源项目和社区 | [团队与社区](#teams)：查看公开成果与参与入口 |
| 了解值得深入的问题 | [前沿方向](#frontiers)：从问题连接到工具、人物与团队 |
| 分享新文章、新闻、论文或试用体验 | [动态与讨论](#discussions) |

**收录说明：** 以下条目于 **2026-10-29** 根据项目仓库、个人主页或机构官网审阅了定位和入口；尚未进行工具实测。收录不构成效果排名或安全认证。后续局部更新在对应条目注明审阅日期，未单独标注的沿用本批日期。软件许可、服务费用及维护状态请以原项目为准。

## AI 安全的两个视角

区别在于 AI 扮演什么角色：**AI 是被保护的系统，还是帮助开展安全工作的工具？**

| 视角 | 含义 | 例子 | 本仓库中的资源 |
| --- | --- | --- | --- |
| **Security for AI：保护 AI 系统** | 保护 AI 模型、Agent、应用、数据及基础设施 | 防止 AI 助手执行网页中的恶意指令，把私密文档泄漏出去 | garak、Agent Scan、NeMo Guardrails、ModelScan |
| **AI for Security：用 AI 做安全** | 用 AI 辅助网络安全工作 | 让 AI Agent 帮助分析人员理解二进制程序、审查代码或调查可疑活动 | REA，将 Agent 连接到逆向工程工具 |

可以这样判断：防止 AI 助手被攻击，属于 **Security for AI**；让这个助手去分析其他软件，属于 **AI for Security**。两个视角可以重叠：执行安全任务的 AI Agent，本身也需要防范恶意输入和过度权限。分类要看资源的用途与分析对象，而不是内部有没有使用 AI。

本仓库同时覆盖这两个视角。另外，有害内容、拒答行为等模型安全评测，与应用是否会泄漏数据、执行未授权操作等系统安全问题，需要分别理解。

<a id="tools"></a>
## 工具 Tools

| 工具 | 类别 | 用途与适用场景 | 使用边界 |
| --- | --- | --- | --- |
| [garak](https://github.com/NVIDIA/garak)<br>![GitHub Repo stars](https://img.shields.io/github/stars/NVIDIA/garak?style=social) | 红队与评测 | LLM 漏洞探测框架，通过多种探针检查提示注入、数据泄漏、越狱等问题；适合建立基础扫描流程 | 结果依赖探针和判定器，需要结合真实应用复核；关联：[NVIDIA](#team-nvidia) |
| [PyRIT](https://github.com/microsoft/PyRIT)<br>![GitHub Repo stars](https://img.shields.io/github/stars/microsoft/PyRIT?style=social) | 红队与评测 | 生成式 AI 风险识别框架，适合编排攻击、目标调用与评分流程 | 需要配置目标与评价标准，不能用一次运行代替完整评估；关联：[Microsoft](#team-microsoft) |
| [promptfoo](https://github.com/promptfoo/promptfoo)<br>![GitHub Repo stars](https://img.shields.io/github/stars/promptfoo/promptfoo?style=social) | 红队与评测 | 提示词、Agent 与 RAG 测试及红队工具，适合配置驱动的回归测试与 CI 集成 | 区分开源功能与托管服务；覆盖范围取决于测试配置与可访问接口 |
| [NeMo Guardrails](https://github.com/NVIDIA-NeMo/Guardrails)<br>![GitHub Repo stars](https://img.shields.io/github/stars/NVIDIA-NeMo/Guardrails?style=social) | 应用防护 | 为 LLM 应用添加可编程的对话与输入输出约束 | 需要针对业务配置和评测；约束层不能替代工具权限控制；关联：[NVIDIA](#team-nvidia) |
| [LLM Guard](https://github.com/protectai/llm-guard)<br>![GitHub Repo stars](https://img.shields.io/github/stars/protectai/llm-guard?style=social) | 应用防护 | LLM 输入输出扫描与处理工具集，覆盖敏感信息及提示注入等检查场景 | 不同扫描器有不同误报、漏报和运行成本，应逐项评估 |
| [Agent Scan](https://github.com/snyk/agent-scan)<br>![GitHub Repo stars](https://img.shields.io/github/stars/snyk/agent-scan?style=social) | Agent 与 MCP 安全 | 扫描 Agent 组件、MCP 服务与 Skills 的安全风险；原 MCP-Scan 项目已迁移至此 | 核验扫描模式的数据处理方式与服务依赖；扫描结果不能代替运行时授权和隔离 |
| [Adversarial Robustness Toolbox（ART）](https://github.com/Trusted-AI/adversarial-robustness-toolbox)<br>![GitHub Repo stars](https://img.shields.io/github/stars/Trusted-AI/adversarial-robustness-toolbox?style=social) | 模型与数据安全 | 机器学习攻防研究工具箱，覆盖规避、投毒、模型提取和隐私推断等研究 | 需确认模型接口和攻击假设；实验结果不直接等同于生产风险 |
| [ModelScan](https://github.com/protectai/modelscan)<br>![GitHub Repo stars](https://img.shields.io/github/stars/protectai/modelscan?style=social) | 模型与数据安全 | 扫描模型序列化文件中的不安全代码，适合模型引入与供应链检查 | 覆盖范围受文件格式与检测规则限制，不能证明模型不存在后门或其他风险 |
| [AgentDojo](https://github.com/ethz-spylab/agentdojo)<br>![GitHub Repo stars](https://img.shields.io/github/stars/ethz-spylab/agentdojo?style=social) | Agent 评测 | 在工具调用任务中评测 Agent 的提示注入攻击与防御 | 需同时观察正常任务完成和攻击效果；关联：[SPY Lab](#team-spylab)、[Florian Tramèr](#person-florian) |
| [HarmBench](https://github.com/centerforaisafety/HarmBench)<br>![GitHub Repo stars](https://img.shields.io/github/stars/centerforaisafety/HarmBench?style=social) | 模型安全评测 | 自动化红队与稳健拒答评测框架，适合研究越狱与模型拒答行为 | 聚焦模型安全行为，结果不能直接代表应用权限或数据隔离安全 |
| [CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks)<br>![GitHub Repo stars](https://img.shields.io/github/stars/meta-llama/PurpleLlama?style=social) | 网络安全评测 | Purple Llama 中的网络安全评测工具集，用于研究模型的相关安全风险与能力 | 各子基准衡量对象不同，比较前应对齐任务与版本；关联：[Meta Purple Llama](#team-meta) |
| [REA（Reverse Engineer Anything）](https://github.com/morluto/rea)<br>![GitHub Repo stars](https://img.shields.io/github/stars/morluto/rea?style=social) | AI 辅助逆向 | 通过 CLI 和 MCP 将编程 Agent 连接到二进制、应用及运行时分析工具，适合 AI 辅助逆向与安全研究；[官网](https://rea.tools/) | 原生分析依赖 Ghidra、Hopper 等引擎及其目标支持范围；运行时采集使用当前用户权限，传给 Agent 的分析结果受其模型供应商的数据政策约束；审阅：2026-10-29 |

<a id="people"></a>
## 人物 People

按姓名字母顺序列出。以可验证的公开成果作为收录依据，关注入口不代表其所有观点均获本仓库认可。默认不记录易变化的雇佣关系。

| 人物 | 关注方向 | 公开成果与跟进入口 |
| --- | --- | --- |
| <a id="person-florian"></a>[Florian Tramèr](https://x.com/florian_tramer) | 对抗机器学习、模型安全与隐私、LLM 攻防 | [SPY Lab](https://spylab.ai/) 负责人；[AgentDojo](https://github.com/ethz-spylab/agentdojo) 共同作者；关联：[Agent 评测](#frontier-evaluation)；[研究与博客](https://floriantramer.com/) |
| [Johann Rehberger](https://x.com/wunderwuzzi23) | 提示注入、数据外泄、AI 应用与 Agent 漏洞 | 持续发布 Embrace The Red 研究与披露；关联：[Agent 信任边界](#frontier-agents)；[研究与博客](https://embracethered.com/blog/) |
| [Kai Greshake](https://x.com/KGreshake) | 间接提示注入、LLM 应用攻击与防御 | 个人博客中的间接注入研究与防御分析；关联：[Agent 信任边界](#frontier-agents)；[研究与博客](https://kai-greshake.de/) |
| [Nicholas Carlini](https://nicholas.carlini.com/) | 对抗机器学习、训练数据隐私、LLM 安全 | 个人主页论文与代码；[可迁移对抗攻击研究](https://llm-attacks.org/)共同作者；关联：[模型与数据安全](#frontier-models) |
| [Simon Willison](https://x.com/simonw) | 提示注入、LLM 应用安全与工程实践 | 持续维护的提示注入专题博客；适合跟进案例与工程分析；关联：[Agent 信任边界](#frontier-agents)；[研究与博客](https://simonwillison.net/tags/prompt-injection/) |

人物姓名优先链接到经过身份核验的 X 账号，研究主页与博客保留在成果栏。Nicholas Carlini 的 X 账号尚未核实，暂保留个人主页。

<a id="teams"></a>
## 团队与社区 Teams

包含研究团队、项目维护团队和开放社区；以公开成果为入口，不作机构实力排名。

| 团队或社区 | 关注方向 | 代表成果与跟进入口 |
| --- | --- | --- |
| <a id="team-spylab"></a>[ETH Zürich SPY Lab](https://spylab.ai/) | 机器学习系统的安全、隐私与可信性 | [AgentDojo](https://github.com/ethz-spylab/agentdojo)；关联：[Florian Tramèr](#person-florian)、[Agent 评测](#frontier-evaluation) |
| <a id="team-meta"></a>[Meta Purple Llama](https://github.com/meta-llama/PurpleLlama) | LLM 安全工具与评测 | [CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks)；关联：[AI for Security](#frontier-cyber) |
| <a id="team-microsoft"></a>[Microsoft PyRIT 项目团队](https://github.com/microsoft/PyRIT) | 生成式 AI 风险识别与红队自动化 | PyRIT 的源码、文档与版本发布；关联：[Agent 评测](#frontier-evaluation) |
| <a id="team-nvidia"></a>[NVIDIA AI 安全工具项目](https://garak.ai/) | 模型漏洞探测与应用约束 | [garak](https://github.com/NVIDIA/garak)、[NeMo Guardrails](https://github.com/NVIDIA-NeMo/Guardrails)；两者为不同项目，分别跟进 |
| [OWASP GenAI Security Project](https://genai.owasp.org/) | 生成式 AI 与 Agent 的风险分类、实践指南和社区协作 | 官网的风险清单、指南与项目入口；适合建立共同术语和评审清单 |

<a id="frontiers"></a>
## 前沿方向 Frontiers

这里记录值得持续研究的问题及其证据入口。以下为编辑选题，不是热度排行榜；代表成果用于理解问题，不表示其中方法仍适用于所有当前模型。每个方向的实效进展与新论文在 Discussions 跟进。

<a id="frontier-agents"></a>
### Agent 的信任边界与间接提示注入

- **核心问题：** 当 Agent 同时读取不可信内容、访问敏感数据并调用工具时，如何限制外部内容对行动的影响？
- **证据入口：** [AgentDojo](https://github.com/ethz-spylab/agentdojo)、[Kai Greshake 的研究](https://kai-greshake.de/)、[Embrace The Red](https://embracethered.com/blog/)。
- **相关资源：** [Simon Willison](https://simonwillison.net/tags/prompt-injection/)、[SPY Lab](#team-spylab)、[Agent Scan](https://github.com/snyk/agent-scan)。
- **开放问题：** 如何把用户授权与模型生成的工具参数关联？防御能否在降低攻击成功率的同时保持正常任务完成率？

### MCP、Skills 与工具供应链

- **核心问题：** 工具描述、服务更新和第三方 Skills 如何进入 Agent 的信任范围，如何验证来源并限制权限？
- **证据入口：** [Agent Scan](https://github.com/snyk/agent-scan) 的项目说明与 [Invariant MCP-Scan 文档](https://github.com/invariantlabs-ai/docs/blob/main/docs/mcp-scan/index.md)中的工具投毒、工具变更和跨工具风险说明。旧文档用于研究背景，当前使用方式以新仓库为准。
- **相关资源：** [OWASP GenAI Security Project](https://genai.owasp.org/)、[AgentDojo](https://github.com/ethz-spylab/agentdojo)。
- **开放问题：** 如何处理工具更新后的重新授权？静态扫描与运行时权限、审计如何衔接？

<a id="frontier-evaluation"></a>
### 面向真实任务的安全评测

- **核心问题：** 如何区分模型越狱、应用被攻破和正常任务失败，并在统一条件下比较防御？
- **证据入口：** [AgentDojo](https://github.com/ethz-spylab/agentdojo)、[HarmBench](https://github.com/centerforaisafety/HarmBench)。两者评测对象不同，应分别解读。
- **相关资源：** [PyRIT](https://github.com/microsoft/PyRIT)、[garak](https://github.com/NVIDIA/garak)、[promptfoo](https://github.com/promptfoo/promptfoo)。
- **开放问题：** 如何控制攻击预算、模型版本和评分器偏差？如何发现基准之外的新攻击面？

<a id="frontier-models"></a>
### 模型、训练数据与制品安全

- **核心问题：** 如何分别评估训练数据泄漏、对抗攻击、模型后门和模型文件加载风险？
- **证据入口：** [Nicholas Carlini 的研究](https://nicholas.carlini.com/)、[ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox)、[ModelScan](https://github.com/protectai/modelscan)。
- **相关资源：** [SPY Lab](#team-spylab)、[可迁移对抗攻击研究](https://llm-attacks.org/)。
- **开放问题：** 如何验证第三方模型的来源与行为？不同层面的检测如何形成可解释的风险证据？文件扫描与行为评测需要分别进行。

<a id="frontier-cyber"></a>
### AI for Security：从能力评测走向真实安全任务

- **核心问题：** 如何评价 AI 在代码安全、漏洞研究与防御任务中的实际价值？
- **证据入口：** [Purple Llama / CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks)。
- **相关团队：** [Meta Purple Llama](#team-meta)。
- **相关工具：** [REA](https://github.com/morluto/rea)，用于通过 Agent 分析二进制与应用行为。
- **开放问题：** 相比已有工具是否带来可验证的增益？如何同时衡量误报、成本、人工复核负担与任务成功率？

<a id="discussions"></a>
## 动态与讨论 Discussions

[进入 Discussions](https://github.com/ikaijua/awesome-ai-security/discussions) · [报告链接或内容问题](https://github.com/ikaijua/awesome-ai-security/issues) · [提交贡献](CONTRIBUTING.zh-CN.md)

新文章、论文、漏洞披露、工具发布、人物访谈与试用体验放在 Discussions；经过审阅、具有长期参考价值的工具和入口沉淀到本页。单篇文章不持续堆入 README。

建议讨论分类：**资源发现、业界动态、实践交流、问题与建议**。每篇分享附原始链接、发布日期、核心信息及值得关注的理由；模板见 [贡献指南](CONTRIBUTING.zh-CN.md#discussion-template)。Discussions 的启用与分类需要在 GitHub 设置中完成，本地文件不会创建这些设置。

## 收录与维护

- 优先引用原项目、研究者和机构的一手来源，描述具体贡献与适用边界。
- 不以 Star、粉丝量或厂商宣传作为单独的收录依据；暂不设置评分和排名。
- 人物需有公开研究、工具或持续技术输出；团队需有可查证的公开成果。
- 新增及修改条目时核验来源与入口。更名迁移更新到当前地址；归档或停止维护的资源保留时注明状态和保留理由。
- 工具实测需另附版本、日期、配置、评价方法和结果；当前条目均仅做来源审阅。
- 鼓励补充不同地区、语言与研究路线的资源；初版覆盖不完整，欢迎基于证据扩展。

完整标准、条目格式和利益关联披露方式见 [CONTRIBUTING.zh-CN.md](CONTRIBUTING.zh-CN.md)。

## 相关资源集

- [muellerberndt/awesome-ai-security](https://github.com/muellerberndt/awesome-ai-security)：覆盖基础学习与多个 AI 安全主题的资源导航。
- [corca-ai/awesome-llm-security](https://github.com/corca-ai/awesome-llm-security)：按攻击、防御等方向整理 LLM 安全论文、评测与工具。
- [chawins/llm-sp](https://github.com/chawins/llm-sp)：LLM 安全与隐私研究资源，包含阅读摘记。
- [turenlabs/secpapers](https://github.com/turenlabs/secpapers)：自动采集并整理 LLM 安全相关论文的目录。

## 许可

本仓库原创编排与文字采用 [CC BY 4.0](LICENSE)。链接指向的论文、代码、商标及其他第三方内容遵循各自许可。
