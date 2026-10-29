# Awesome AI Security

**English** | [简体中文](README.zh-CN.md)

**Discover AI security tools, people, teams, and research frontiers worth following.**

A curated resource map for security engineers, researchers, and AI application developers. Focused on LLM, agent, and AI application security, with coverage of model and data security and the use of AI in cybersecurity.

[Tools](#tools) · [People](#people) · [Teams & Communities](#teams) · [Frontiers](#frontiers) · [Discussions](#discussions) · [Contributing](CONTRIBUTING.md)

## How to use this list

| Your goal | Start here |
| --- | --- |
| Choose evaluation and protection tools for AI applications | [Tools](#tools): browse by use case and consider each tool's limitations |
| Follow researchers and their work | [People](#people): explore X profiles, blogs, and representative work |
| Find research teams, open-source projects, and communities | [Teams & Communities](#teams): explore public work and participation channels |
| Identify problems worth investigating | [Frontiers](#frontiers): connect research questions to tools, people, and teams |
| Share articles, news, papers, or hands-on experience | [Discussions](#discussions) |

**Review status:** The entries below were reviewed on **2026-10-29** against project repositories, personal websites, or official institutional sources for their scope and reference links. Tools have not been tested by this repository. Inclusion is neither a performance ranking nor a security certification. Subsequent updates should carry an entry-specific review date; entries without one use this batch date. Consult the original projects for software licenses, service fees, and maintenance status.

## Two perspectives on AI security

The distinction is the role AI plays: **is AI the system being protected, or a tool used for security work?**

| Perspective | What it means | Example | Resources in this list |
| --- | --- | --- | --- |
| **Security for AI** | Protect AI models, agents, applications, data, and infrastructure | Prevent an AI assistant from following malicious instructions in a web page and leaking private documents | garak, Agent Scan, NeMo Guardrails, ModelScan |
| **AI for Security** | Use AI to assist cybersecurity tasks | Have an AI agent help an analyst understand a binary, review code, or investigate suspicious activity | REA, which connects agents to reverse-engineering tools |

A practical check: preventing an AI assistant from being compromised is **Security for AI**; using that assistant to investigate other software is **AI for Security**. These perspectives can overlap: an AI-powered security agent also needs protection against malicious inputs and excessive permissions. Classify a resource by its purpose and target, rather than whether it uses AI internally.

This list covers both perspectives. It also distinguishes system security from model safety evaluations such as harmful-content and refusal testing; those evaluations answer different questions from whether an application can leak data or perform unauthorized actions.

<a id="tools"></a>
## Tools

| Tool | Category | Purpose and use cases | Limitations and considerations |
| --- | --- | --- | --- |
| [garak](https://github.com/NVIDIA/garak)<br>![GitHub Repo stars](https://img.shields.io/github/stars/NVIDIA/garak?style=social) | Red teaming & evaluation | LLM vulnerability scanner with probes for prompt injection, data leakage, jailbreaks, and other weaknesses; useful for baseline scanning | Results depend on probes and detectors and require validation against the actual application; related: [NVIDIA](#team-nvidia) |
| [PyRIT](https://github.com/microsoft/PyRIT)<br>![GitHub Repo stars](https://img.shields.io/github/stars/microsoft/PyRIT?style=social) | Red teaming & evaluation | Generative AI risk identification framework for orchestrating attacks, target interactions, and scoring | Requires target configuration and evaluation criteria; one run does not constitute a complete assessment; related: [Microsoft](#team-microsoft) |
| [promptfoo](https://github.com/promptfoo/promptfoo)<br>![GitHub Repo stars](https://img.shields.io/github/stars/promptfoo/promptfoo?style=social) | Red teaming & evaluation | Testing and red teaming for prompts, agents, and RAG systems, with configuration-driven regression testing and CI integration | Distinguish open-source capabilities from hosted services; coverage depends on test configuration and accessible interfaces |
| [NeMo Guardrails](https://github.com/NVIDIA-NeMo/Guardrails)<br>![GitHub Repo stars](https://img.shields.io/github/stars/NVIDIA-NeMo/Guardrails?style=social) | Application protection | Programmable conversation and input/output constraints for LLM applications | Requires application-specific configuration and evaluation; guardrails do not replace tool permission controls; related: [NVIDIA](#team-nvidia) |
| [LLM Guard](https://github.com/protectai/llm-guard)<br>![GitHub Repo stars](https://img.shields.io/github/stars/protectai/llm-guard?style=social) | Application protection | Input/output scanning and processing toolkit for LLM interactions, including sensitive information and prompt injection checks | Scanners differ in false positives, false negatives, and operating cost; evaluate each for the intended use case |
| [Agent Scan](https://github.com/snyk/agent-scan)<br>![GitHub Repo stars](https://img.shields.io/github/stars/snyk/agent-scan?style=social) | Agent & MCP security | Security scanning for agent components, MCP servers, and skills; the former MCP-Scan project has moved here | Review data handling and service dependencies for the chosen scanning mode; scanning does not replace runtime authorization and isolation |
| [Adversarial Robustness Toolbox (ART)](https://github.com/Trusted-AI/adversarial-robustness-toolbox)<br>![GitHub Repo stars](https://img.shields.io/github/stars/Trusted-AI/adversarial-robustness-toolbox?style=social) | Model & data security | Machine learning security research toolkit covering evasion, poisoning, model extraction, and privacy inference | Check model interfaces and attack assumptions; experimental results do not directly establish production risk |
| [ModelScan](https://github.com/protectai/modelscan)<br>![GitHub Repo stars](https://img.shields.io/github/stars/protectai/modelscan?style=social) | Model & data security | Scans serialized model files for unsafe code; useful when importing models and reviewing the model supply chain | Coverage depends on supported formats and detection rules; a clean scan does not establish the absence of backdoors or other risks |
| [AgentDojo](https://github.com/ethz-spylab/agentdojo)<br>![GitHub Repo stars](https://img.shields.io/github/stars/ethz-spylab/agentdojo?style=social) | Agent evaluation | Evaluates prompt injection attacks and defenses for agents performing tool-use tasks | Examine both legitimate task completion and attack outcomes; related: [SPY Lab](#team-spylab), [Florian Tramèr](#person-florian) |
| [HarmBench](https://github.com/centerforaisafety/HarmBench)<br>![GitHub Repo stars](https://img.shields.io/github/stars/centerforaisafety/HarmBench?style=social) | Model safety evaluation | Automated red teaming and robust refusal evaluation framework for studying jailbreaks and model refusal behavior | Focuses on model safety behavior; results do not directly establish application permission or data isolation security |
| [CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks)<br>![GitHub Repo stars](https://img.shields.io/github/stars/meta-llama/PurpleLlama?style=social) | Cybersecurity evaluation | Cybersecurity evaluation suite within Purple Llama for studying model-related security risks and capabilities | Sub-benchmarks measure different properties; align tasks and versions before comparing results; related: [Meta Purple Llama](#team-meta) |
| [REA (Reverse Engineer Anything)](https://github.com/morluto/rea)<br>![GitHub Repo stars](https://img.shields.io/github/stars/morluto/rea?style=social) | AI-assisted reverse engineering | CLI and MCP tools connecting coding agents to binary, application, and runtime analysis; useful for AI-assisted reverse engineering and security investigation; [official website](https://rea.tools/) | Native analysis depends on engines such as Ghidra or Hopper and their supported targets; runtime capture uses the user's permissions, and analysis results passed to the agent are subject to its model provider's data policy; reviewed: 2026-10-29 |

<a id="people"></a>
## People

Listed alphabetically by name, based on verifiable public contributions. Links for following someone's work do not imply endorsement of all their views. Employment affiliations are generally omitted because they can change.

| Person | Focus | Representative work and channels |
| --- | --- | --- |
| <a id="person-florian"></a>[Florian Tramèr](https://x.com/florian_tramer) | Adversarial ML, model security and privacy, LLM attacks and defenses | Leads [SPY Lab](https://spylab.ai/); co-author of [AgentDojo](https://github.com/ethz-spylab/agentdojo); related: [agent evaluation](#frontier-evaluation); [Research and blog](https://floriantramer.com/) |
| [Johann Rehberger](https://x.com/wunderwuzzi23) | Prompt injection, data exfiltration, AI application and agent vulnerabilities | Research and disclosures on Embrace The Red; related: [agent trust boundaries](#frontier-agents); [Research and blog](https://embracethered.com/blog/) |
| [Kai Greshake](https://x.com/KGreshake) | Indirect prompt injection, attacks and defenses for LLM applications | Research and defense analysis on his personal blog; related: [agent trust boundaries](#frontier-agents); [Research and blog](https://kai-greshake.de/) |
| [Nicholas Carlini](https://nicholas.carlini.com/) | Adversarial ML, training data privacy, LLM security | Papers and code on his personal website; co-author of research on [transferable adversarial attacks](https://llm-attacks.org/); related: [model and data security](#frontier-models) |
| [Simon Willison](https://x.com/simonw) | Prompt injection, LLM application security, engineering practice | Ongoing prompt injection coverage with case studies and engineering analysis; related: [agent trust boundaries](#frontier-agents); [Research and blog](https://simonwillison.net/tags/prompt-injection/) |

Names link to verified X profiles where available; research websites and blogs remain in the work column. An X account for Nicholas Carlini has not been verified, so his personal website is retained.

<a id="teams"></a>
## Teams & Communities

Research groups, project teams, and open communities, linked through their public work. This is not an institutional ranking.

| Team or community | Focus | Representative work and channels |
| --- | --- | --- |
| <a id="team-spylab"></a>[ETH Zürich SPY Lab](https://spylab.ai/) | Security, privacy, and trustworthiness of machine learning systems | [AgentDojo](https://github.com/ethz-spylab/agentdojo); related: [Florian Tramèr](#person-florian), [agent evaluation](#frontier-evaluation) |
| <a id="team-meta"></a>[Meta Purple Llama](https://github.com/meta-llama/PurpleLlama) | LLM security tools and evaluation | [CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks); related: [AI for Security](#frontier-cyber) |
| <a id="team-microsoft"></a>[Microsoft PyRIT project team](https://github.com/microsoft/PyRIT) | Generative AI risk identification and red teaming automation | PyRIT source code, documentation, and releases; related: [agent evaluation](#frontier-evaluation) |
| <a id="team-nvidia"></a>[NVIDIA AI security tool projects](https://garak.ai/) | Model vulnerability scanning and application guardrails | [garak](https://github.com/NVIDIA/garak) and [NeMo Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) are separate projects to follow individually |
| [OWASP GenAI Security Project](https://genai.owasp.org/) | Risk taxonomies, practical guidance, and community collaboration for generative AI and agents | Risk lists, guides, and project channels for shared terminology and review checklists |

<a id="frontiers"></a>
## Frontiers

Research questions worth following, with supporting sources. These are editorial selections, not a popularity ranking. Representative work helps explain the problems; its methods may not apply to every current model. Follow new papers and practical developments in Discussions.

<a id="frontier-agents"></a>
### Agent trust boundaries and indirect prompt injection

- **Core question:** When an agent reads untrusted content, accesses sensitive data, and calls tools, how can external content be prevented from steering its actions?
- **Evidence:** [AgentDojo](https://github.com/ethz-spylab/agentdojo), [Kai Greshake's research](https://kai-greshake.de/), and [Embrace The Red](https://embracethered.com/blog/).
- **Related resources:** [Simon Willison](https://simonwillison.net/tags/prompt-injection/), [SPY Lab](#team-spylab), and [Agent Scan](https://github.com/snyk/agent-scan).
- **Open questions:** How can user authorization be bound to model-generated tool arguments? Can defenses reduce attack success while preserving legitimate task completion?

### MCP, skills, and the tool supply chain

- **Core question:** How do tool descriptions, service updates, and third-party skills enter an agent's trust boundary, and how can their origins be verified and permissions limited?
- **Evidence:** The [Agent Scan](https://github.com/snyk/agent-scan) project and [Invariant MCP-Scan documentation](https://github.com/invariantlabs-ai/docs/blob/main/docs/mcp-scan/index.md) on tool poisoning, tool changes, and cross-tool risks. The older documentation provides research context; consult the current repository for usage.
- **Related resources:** [OWASP GenAI Security Project](https://genai.owasp.org/) and [AgentDojo](https://github.com/ethz-spylab/agentdojo).
- **Open questions:** How should authorization be renewed after tool updates? How should static scanning connect to runtime permissions and auditing?

<a id="frontier-evaluation"></a>
### Security evaluation grounded in real tasks

- **Core question:** How can evaluations distinguish model jailbreaks, application compromise, and legitimate task failure, and compare defenses under consistent conditions?
- **Evidence:** [AgentDojo](https://github.com/ethz-spylab/agentdojo) and [HarmBench](https://github.com/centerforaisafety/HarmBench) evaluate different properties and should be interpreted separately.
- **Related resources:** [PyRIT](https://github.com/microsoft/PyRIT), [garak](https://github.com/NVIDIA/garak), and [promptfoo](https://github.com/promptfoo/promptfoo).
- **Open questions:** How should attack budgets, model versions, and evaluator bias be controlled? How can evaluations uncover attack surfaces beyond existing benchmarks?

<a id="frontier-models"></a>
### Models, training data, and artifact security

- **Core question:** How should training data leakage, adversarial attacks, model backdoors, and model-loading risks each be evaluated?
- **Evidence:** [Nicholas Carlini's research](https://nicholas.carlini.com/), [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox), and [ModelScan](https://github.com/protectai/modelscan).
- **Related resources:** [SPY Lab](#team-spylab) and research on [transferable adversarial attacks](https://llm-attacks.org/).
- **Open questions:** How can the origin and behavior of third-party models be verified? How can detection at different layers provide interpretable risk evidence? File scanning and behavioral evaluation require separate assessments.

<a id="frontier-cyber"></a>
### AI for Security: from capability benchmarks to real security tasks

- **Core question:** How can the practical value of AI in code security, vulnerability research, and defensive tasks be evaluated?
- **Evidence:** [Purple Llama / CyberSecEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks).
- **Related team:** [Meta Purple Llama](#team-meta).
- **Related tool:** [REA](https://github.com/morluto/rea) for investigating binaries and application behavior with agents.
- **Open questions:** Does AI deliver verifiable improvements over existing tools? How should false positives, cost, human review effort, and task success be measured together?

<a id="discussions"></a>
## Discussions

[Join Discussions](https://github.com/ikaijua/awesome-ai-security/discussions) · [Report an issue](https://github.com/ikaijua/awesome-ai-security/issues) · [Contribute](CONTRIBUTING.md)

Use Discussions for new articles, papers, vulnerability disclosures, tool releases, interviews, and hands-on experience. Reviewed tools and reference links with lasting value belong on this page. Individual articles are not continuously added to the README.

Suggested categories: **Resource Discoveries, Industry Updates, Hands-on Experience, and Questions & Suggestions**. Include the original source, publication date, key information, and why it matters; see the [sharing template](CONTRIBUTING.md#discussion-template). Discussions and its categories must be enabled in GitHub settings; local files do not create these settings.

## Curation and maintenance

- Prefer primary sources from original projects, researchers, and institutions. Describe specific contributions and limitations.
- Stars, follower counts, and vendor claims are not sufficient grounds for inclusion. This list currently has no scores or rankings.
- People should have public research, tools, or sustained technical contributions; teams should have verifiable public work.
- Check sources and links when adding or updating entries. Use current URLs after renames or migrations; note the status and reason for retaining archived or discontinued resources.
- Hands-on evaluations require versions, dates, configuration, methodology, and results. Current entries have only undergone source review.
- Contributions across regions, languages, and research approaches are welcome. Initial coverage is incomplete; help expand it with evidence.

See [CONTRIBUTING.md](CONTRIBUTING.md) for full criteria, entry formats, and disclosure of affiliations.

## Related resource lists

- [muellerberndt/awesome-ai-security](https://github.com/muellerberndt/awesome-ai-security): resources spanning foundational learning and multiple AI security topics.
- [corca-ai/awesome-llm-security](https://github.com/corca-ai/awesome-llm-security): LLM security papers, benchmarks, and tools organized around attacks, defenses, and related areas.
- [chawins/llm-sp](https://github.com/chawins/llm-sp): LLM security and privacy research resources with reading notes.
- [turenlabs/secpapers](https://github.com/turenlabs/secpapers): an automatically collected and organized catalog of LLM security research papers.

## License

Original text and compilation are licensed under [CC BY 4.0](LICENSE). Linked papers, code, trademarks, and other third-party materials retain their respective licenses.
