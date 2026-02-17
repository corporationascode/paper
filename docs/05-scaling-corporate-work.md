---
title: "VI. Scaling Corporate Work: Founders, Agents, and the One-Person Unicorn"
nav_order: 7
layout: default
---
# VI. Scaling Corporate Work: Founders, Agents, and the One-Person Unicorn

The corporation-as-code model offers clear benefits in precision, auditability, and interoperability. But its most compelling application may be in enabling a new category of organization: the highly capitalized company with minimal human staff.

## The Rise of Solo Founders

For decades, conventional startup wisdom held that companies need co-founders. Y Combinator practically mandated them.[^0] Venture capitalists viewed solo founders with suspicion, interpreting a single founder as a sign that the entrepreneur could not convince anyone else to join their mission. The lone founder was a red flag.

The data suggests a shift.

According to an analysis of Carta data (Carta being a leading equity management platform) published by Solo Founders, solo founders accounted for 36.3% of new startups formed in the first half of 2025, up from 23.7% in 2019.[^1] It bears noting that the organization Solo Founders has a stake in promoting data showing this growth, and comprehensive data on this trend remains limited. Still, the trend has sparked discussion in founder communities, with many pointing to AI-powered tools as a possible enabler.[^1b]

If these figures are accurate, the trajectory is notable: 24.5% in 2020, 26.0% in 2021, 27.2% in 2022, 27.8% in 2023, 30.5% in 2024, and now 36.3%. More than a third of new venture-backed companies may now be founded by individuals working alone.

The question is why, and what it means for corporate infrastructure.

## Corporate Scalability

Startups have long obsessed over "technical scalability": the ability to serve more users without proportionally increasing infrastructure costs. A well-architected software system can serve a million users as easily as a thousand. This leverage is fundamental to the economics of technology companies.

But technical scalability has a less glamorous counterpart: corporate scalability. As companies grow, so do their administrative burdens. Capitalization tables become complex. Regulatory filings multiply. Board meetings require documentation. Equity grants demand tracking. Compliance deadlines accumulate. Traditionally, managing this complexity required either dedicated staff or expensive professional services.

For solo founders, corporate administration presents a particular challenge. While they can certainly engage professional services, cost constraints often mean they remain heavily involved in the process to minimize expenses. A single person building a product cannot simultaneously manage a minute book, track vesting schedules, prepare board consents, and file annual reports. The result is either administrative neglect (creating problems for future fundraising or exits) or excessive time diverted from core business activities.

The corporation-as-code model addresses this problem directly. If corporate state is represented as structured data, administrative tasks become amenable to automation. Generating a cap table summary is a database query, not a document review exercise. Filing a state annual report can be triggered automatically from the corporate record. Tracking compliance deadlines becomes a matter of configuration rather than calendar management.

In other words, corporation-as-code enables corporate scalability: the ability to maintain institutional-grade governance without proportionally increasing administrative overhead.

## AI Agents and Corporate Operations

The timing of the solo founder trend is not coincidental. It corresponds with dramatic advances in AI capabilities, particularly in agentic systems capable of executing complex, multi-step tasks autonomously.

Frontier models released in late 2025 represent a step change in what AI agents can accomplish.[^2] These systems excel at autonomous, multi-step tasks requiring sustained reasoning. They achieve higher success rates on real-world software engineering benchmarks while using significantly fewer computational resources. They coordinate multiple tools, maintain context across extended operations, and resist adversarial manipulation better than their predecessors.

The relevance to corporate operations is direct. If AI agents can reliably maintain and modify complex codebases (navigating dependencies, running tests, fixing bugs, committing changes), they can perform analogous operations on corporate data structures. A corporate repository is, in many ways, simpler than a software repository. The schema is more constrained. The validation rules are clearer. The operations (issue shares, appoint director, file report) are more standardized.

Consider what becomes possible when corporate state is structured and AI agents are capable:

**Routine administration** can be delegated. The agent monitors the corporate record, identifies upcoming deadlines, prepares required filings, and presents them for human approval. The founder reviews and approves rather than researches and drafts.

**Compliance monitoring** becomes continuous. Rather than periodic audits, the agent continuously validates that the corporate state conforms to applicable rules. Missing signatures, lapsed registrations, or incomplete records trigger alerts before they become problems.

**Transaction preparation** accelerates. When a financing round approaches, the agent assembles the required information from the corporate record, identifies discrepancies that need resolution, and prepares documentation in the formats investors and their counsel expect.

**Governance documentation** is generated on demand. Board minutes, written consents, and shareholder resolutions can be drafted from structured inputs describing the actions taken. The human reviews and signs; the agent handles formatting and filing.

None of this requires artificial general intelligence or science fiction scenarios. It requires only that corporate information be structured (enabling programmatic access) and that AI agents be capable of multi-step tasks with appropriate oversight (which current systems demonstrate).

## The One-Person Unicorn

The logical endpoint of these trends is the "one-person unicorn": a billion-dollar company operated by a single founder, supported by AI agents and external service providers, with minimal or no traditional employees.

This is not purely speculative. We already see venture-backed companies with valuations in the hundreds of millions operated by teams of fewer than ten people. As AI capabilities expand and corporate administration becomes more automatable, the minimum viable team size continues to shrink.

To be clear: even a solo founder will likely engage outside counsel for significant transactions, complex governance questions, and regulatory filings that require professional judgment. The one-person unicorn does not mean the one-person legal department. What changes is the interface between founder and counsel. Instead of exchanging documents back and forth, counsel operates on the same structured corporate repository. The lawyer reviews the data model, validates proposed transactions against it, and commits changes that the founder approves. The founder is not reading minute books; neither is the lawyer recreating corporate history from scattered PDFs.

For such organizations, document-centric corporate infrastructure creates unnecessary friction. A solo founder cannot spend hours managing PDFs and coordinating signatures across multiple platforms. Paper-emulating workflows are incompatible with the operating model these founders are building, even when professional services handle the details.

Corporation-as-code offers an alternative. From incorporation, the corporate state exists as structured data. Lawyers, accountants, and AI agents all operate on the same authoritative record. Documents are generated when needed but are not the source of truth. The founder's attention remains on the business; professional advisors access a clean, queryable corporate record rather than reconstructing it from documents each time.

This vision is not limited to solo founders. Any organization seeking to minimize administrative overhead while maintaining governance rigor can benefit. But the solo founder represents the limiting case: if corporation-as-code can work for a single person running a substantial business, it can work for organizations of any size.

## Adoption Dynamics

Retrofitting existing corporations into a code-native model presents challenges. Legacy organizations have accumulated years of document-based records. Converting this history to structured data requires effort that may not be justified for mature companies with established administrative processes.

New corporations face no such barrier. A company formed today can be born digital in the fullest sense. Its initial state can be recorded as structured data. Every subsequent change can be captured as a commit to the corporate repository. Documents can be generated as needed for regulatory filings or third-party interactions, but the structured record remains authoritative.

Competition may accelerate adoption, but the dynamics are more consequential than mere efficiency gains suggest. Consider the economics of a venture-backed technology company: constant financing rounds, option grants, refreshes, restructures, heavy board cadence, investor governance requirements. Each transaction requires documentation, due diligence, and coordination. In a document-centric model, each transaction consumes legal fees, management attention, and time. In a corporation-as-code model, transaction preparation becomes a data query; due diligence becomes API access; closing becomes a commit.

The velocity difference is substantial. A startup with structured corporate records can close a financing round in a fraction of the time required by document-centric competitors. They can respond to acquisition inquiries with instant data room generation. They can onboard investors without weeks of document assembly. Faster fundraising translates directly to competitive advantage: a company that closes rounds quickly can deploy capital sooner, scale ARR faster, and reach defensible positions before slower competitors.

The impact extends beyond individual transactions. Reduced administrative overhead means resources can be redeployed to higher-ROI work. Lower fixed costs reduce liquidity risk and improve operating leverage. Faster transactions reduce the friction costs of consolidation and restructuring. By compressing diligence and closing overhead, structured corporate records lower the threshold at which solo-founder ventures become viable.

Private investment funds represent another particularly compelling early adoption case. Fund formation involves repetitive processes: similar limited partnership agreements, standardized terms, predictable capital call and distribution mechanics, and dense webs of investor-specific obligations (side letters, most-favored-nation provisions, co-investment rights). A fund administrator managing dozens of funds with hundreds of limited partners faces exactly the kind of complexity that structured data handles well. Fund terms are a particularly clear case because they generate recurring, exception-heavy administration. When rights and elections (e.g., MFNs, reporting elections, fee and expense terms, consent thresholds) are represented as structured data rather than prose, sponsors can query obligations across the LP base, drive notices and elections from the record itself, and reconcile outcomes directly into fund administration and accounting workflows. The result is not just fewer errors, it is a lower marginal cost of operating the fund, compressing the GP's administrative burden and the fees required to support it.

The adoption path, then, likely begins with new formations rather than legacy conversions, with private investment funds and venture-backed startups as natural beachheads. As more founders and fund managers choose code-native infrastructure, the ecosystem of supporting tools, service providers, and regulatory accommodations will develop. Over time, the benefits may become compelling enough to justify conversion even for established organizations.

The solo founder trend suggests demand exists. The AI agent trend suggests capability is emerging. Corporation-as-code provides the conceptual framework connecting them.

[^0]: The conventional wisdom that startups need co-founders was widely discussed in the startup community. See, e.g., "Question re solo founders: 'A startup is too much work for one person,'" Hacker News, 2015. https://news.ycombinator.com/item?id=9239322
[^1]: Dutilh, Ari. "Solo Founders in 2025: Why One-Third of All Startups Are Flying Solo." Solo Founders, December 30, 2025. https://solofounders.com/blog/solo-founders-in-2025-why-one-third-of-all-startups-are-flying-solo
[^1b]: The "one-person unicorn" concept generated extensive discussion on Hacker News when Sam Altman suggested a one-person billion-dollar company was imminent. See Devin Coldewey, "Sam Altman says the 'one-person unicorn' could soon be a reality," TechCrunch, January 7, 2025. https://techcrunch.com/2025/01/07/sam-altman-says-the-one-person-unicorn-could-soon-be-a-reality/
[^2]: Anthropic, "Introducing Claude Opus 4.5," https://www.anthropic.com/news/claude-opus-4-5
