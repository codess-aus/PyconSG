# Merlions, Agents & Copilot

![Cover art for Merlions, Agents & Copilot](assets/1-Title.png){ .chapter-hero }

> **A standalone guide to building trustworthy Python agents on Azure.**
> Read it cover to cover, or jump to the chapter you need. Each chapter pairs a
> concept with clear, copyable instructions so you can build the same patterns
> yourself, no presentation required.
>
> Everything here is grounded in current Microsoft Build 2026 guidance and in
> the working repository content under [chapters](chapters/README.md).

## Chapter index

| # | Chapter | Theme |
|---|---|---|
| 1 | [Why trust?](chapters/01-title.md) | Framing |
| 2 | [What we'll explore](chapters/02-agenda.md) | Framing |
| 3 | [Meet our agents](chapters/03-agents.md) | Cast |
| 4 | [Multi-agent systems](chapters/04-multiagent.md) | Architecture |
| 5 | [GitHub Copilot to the rescue](chapters/05-github-copilot.md) | Tooling |
| 6 | [Trust is our architectural style](chapters/06-trust.md) | Pattern |
| 7 | [Walkthrough: Copilot scaffolds the safe parts](chapters/07-demo-copilot.md) | Hands-on |
| 8 | [Hawker Recommender agent](chapters/08-hawker-agent.md) | Agent |
| 9 | [Haze Tracker agent](chapters/09-haze-agent.md) | Agent |
| 10 | [Merlion Wisecracker agent](chapters/10-wisecracker-agent.md) | Agent |
| 11 | [From local to cloud: Azure](chapters/11-azure-deploy.md) | Deployment |
| 12 | [Observe. Evaluate. Improve.](chapters/12-observe.md) | Operations |
| 13 | [Where to go from here](chapters/13-call-to-action.md) | Close |

## The one-paragraph version

Build **small, specialised agents** instead of one mega-agent. Give each one
**least-privilege tools, grounded retrieval, and citations**. Make
**transparency, safety, reliability, and observability** the architectural
style, designed in, not bolted on. Use **GitHub Copilot** to generate the
boring, safety-critical scaffolding. Ship to **Azure** with **OpenTelemetry**
tracing and **continuous evaluation** from day one. The Build 2026 mantra:
*Observe. Evaluate. Improve. Roll out safely. Repeat.*
