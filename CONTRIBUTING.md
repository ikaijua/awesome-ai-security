# Contributing

**English** | [简体中文](CONTRIBUTING.zh-CN.md)

[Back to the resource list](README.md)

Help discover useful AI security tools, people and teams worth following, and research frontiers supported by evidence.

## Where content belongs

| Content | Destination |
| --- | --- |
| Tools, people, teams, and lasting research directions | Update the README and submit a pull request |
| New articles, papers, news, releases, and hands-on observations | [Discussions](https://github.com/ikaijua/awesome-ai-security/discussions) |
| Broken links, inaccurate descriptions, and maintenance tasks | [Issues](https://github.com/ikaijua/awesome-ai-security/issues) |

Keep each PR focused on one resource or a related set of changes. If inclusion is uncertain, start a Discussion.

## Inclusion criteria

1. Resources must directly concern AI system security, model and data security, or the use of AI in cybersecurity.
2. Provide at least one accessible primary source: an official repository, personal website, institutional website, or original paper.
3. Explain the problem addressed, public contribution, or use case. Avoid unsupported claims such as “the best” or “completely secure.”
4. Tools must have inspectable code, documentation, or a usable entry point; a promotional page alone is insufficient. Identify commercial services and do not imply all features are free or open source.
5. People should have specific research, projects, or sustained technical contributions; teams should have specific public work. Prefer stable websites and do not infer current employment from historical work.
6. Research frontiers need supporting research or case evidence and open questions. Distinguish observed facts from editorial judgment.
7. Stars, follower counts, sponsorship, and personal connections are not inclusion criteria. Authors, employees, investors, and other affiliated submitters should disclose their relationship in the PR. Disclosed affiliations do not prevent review under the same criteria.

## Bilingual maintenance

[README.md](README.md) is the default English homepage; [README.zh-CN.md](README.zh-CN.md) is the Chinese version. The contribution guide is also available in both languages. Keep entries, original URLs, explicit anchors, and review dates synchronized when adding, removing, or updating resources. Language switches and contribution links should target the matching version. Translations must preserve the strength of the evidence and the stated limitations. Discussions may be in English or Chinese; duplicate posts are not required.

## Entry formats

Match the columns of the relevant README table. Be concise and summarize in your own words. Link directly to original sources without referral or tracking parameters.

**Tools:**

Keep all tools and benchmarks in a single table. Use the Category column to distinguish use cases rather than creating separate subsection tables.

For tools hosted on GitHub, add a dynamic Shields.io star badge below the name in the same cell using `<br>`. Use `https://img.shields.io/github/stars/OWNER/REPO?style=social`, replacing `OWNER/REPO` with the actual repository. For a tool in a repository subdirectory, use the parent repository and its star count. Keep badges synchronized across languages. Stars provide context and are not a quality score.

```markdown
| [Name](official-repository-or-documentation) | Category | Problem addressed and use cases | Requirements, limitations, and related teams; reviewed: YYYY-MM-DD |
```

**People:**

Prefer a verified X profile for the name link and retain the personal website or blog in the work column. Verify identity through links from the person's website or a profile linked to their official website; never guess handles. Fall back to the personal website and note when an X account cannot be verified.

```markdown
| [Name](verified-x-profile-or-personal-website) | Research or practical focus | Representative work, channels, and related frontiers; reviewed: YYYY-MM-DD |
```

**Teams and communities:**

```markdown
| [Team name](official-website) | Main focus | Representative projects, research, and related people; reviewed: YYYY-MM-DD |
```

**Frontiers:**

```markdown
### Direction name

- **Core question:** What problem needs to be solved?
- **Evidence:** Original papers, research projects, or disclosures.
- **Related resources:** Links to tools, people, and teams already listed.
- **Open questions:** What does the available evidence leave unanswered?
- **Last reviewed:** YYYY-MM-DD.
```

A review date means sources, scope, and links were checked. It does not mean a tool was tested or its security verified. For hands-on findings, share model and tool versions, run dates, configuration, budget, evaluation methods, and failure cases in a Discussion, then link to it from the entry.

<a id="discussion-template"></a>
## Discussion sharing template

```markdown
## Source

- Original URL:
- First published: YYYY-MM-DD
- Event date: YYYY-MM-DD (if applicable)
- Shared on: YYYY-MM-DD
- Related tools / people / teams / frontiers:

## Key information

Summarize in your own words. Distinguish the source's conclusions from your interpretation.

## Why it matters

Explain what is new, applicable conditions, and known limitations.

## Observations or questions to investigate

For hands-on work, include versions, configuration, and results. Disclose any affiliations here.
```

## Maintenance rules

- Check primary sources and add a review date when creating or updating entries. Initial README entries without individual dates use the batch date at the top of the page.
- Update migrated resources to their current official URLs. Retain former names when useful for discovery.
- Mark archived or discontinued resources. Keep them if they retain research value and explain why; remove unavailable resources when no trustworthy replacement source can be found.
- Resolve disputes in PRs or Issues using primary sources. Unsupported promotional claims do not belong in the list. Include evidence and reasoning for corrections.
- Periodically check links and scope by section. The initial version does not promise a fixed update schedule. Submit actual review findings rather than date-only changes.
- Original contributions are provided under this repository's CC BY 4.0 license. Respect third-party licenses; prefer summaries and links over reproducing full content.

## Setting up GitHub Discussions

Local Markdown files do not enable Discussions or create categories. Repository administrators can enable Discussions under Settings → General → Features, then create these categories:

| Category | Suggested format | Purpose |
| --- | --- | --- |
| Resource Discoveries | Open-ended discussion | Articles, papers, tools, people, and team recommendations |
| Industry Updates | Open-ended discussion | Disclosures, releases, research developments, and standards |
| Hands-on Experience | Open-ended discussion | Tool trials, reproductions, failure cases, and comparisons |
| Questions & Suggestions | Q&A | Usage questions, tool selection, and repository suggestions |

Consider a pinned welcome post with the project scope, sharing template, and curation process.
