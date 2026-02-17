---
title: "III. Existing Approaches and Their Limits"
nav_order: 4
layout: default
---
# III. Existing Approaches and Their Limits

The vision outlined in the previous sections is not without precedent. Legal technology has evolved considerably over the past two decades, and several categories of tools now address corporate data management, entity governance, and legal process automation. Yet these existing approaches, while useful, fall short of treating the corporation as a first-class software object. They digitize workflows without challenging the underlying document-centric paradigm, and they often introduce new problems (vendor lock-in, proprietary formats, siloed data) even as they solve old ones.

## Entity Management Software

The most direct attempt to manage corporate information as data comes from entity management platforms. Products like Carta, Athennian, Diligent Entities, and similar tools offer centralized databases for tracking corporate structures, cap tables, officer appointments, and compliance deadlines. These platforms store information in structured form behind their interfaces, generating documents (stock certificates, board consents, annual filings) as outputs.

In principle, this sounds like the corporation-as-code model described earlier. In practice, the resemblance is superficial.

First, these tools replicate paper workflows behind graphical interfaces. The user experience often mirrors the traditional process: draft a resolution, circulate for signature, file with the state. The underlying data model exists to support document generation, not to serve as the authoritative representation of the corporation. The document remains the deliverable; the database is merely a convenience.

Second, the data models are proprietary. Each platform defines its own schema, its own entity relationships, its own conventions for representing corporate structures. There is no interoperability between systems. Moving from one platform to another requires exporting documents (often as PDFs) and re-entering information manually. The structured data, which ought to be the corporation's most portable asset, remains inside a vendor's system.

Third, practical friction accumulates. The total cost of document-based corporate management extends far beyond obvious line items. Subscription fees for entity management platforms compound annually. Migration between platforms requires consulting engagements to map data, validate completeness, and reconcile discrepancies. IT teams spend cycles maintaining integrations, managing access controls, and troubleshooting sync failures across vendor clouds. Legal fees accrue each time a lawyer must reconstruct corporate history from scattered documents, verify consistency between a cap table and underlying agreements, or prepare a data room for due diligence. Error costs are particularly insidious: a miskeyed share number, an overlooked amendment, a filing deadline missed because it lived in a spreadsheet rather than an integrated system. These errors surface at the worst moments (closings, audits, disputes) when the cost of correction is highest. Export capabilities, while improving, often produce lossy representations: flattened spreadsheets, PDF archives, or formats that cannot be meaningfully imported elsewhere.[^1] While data portability is now a widespread statutory requirement (including under the GDPR), its limited scope and technical carve-outs rarely guarantee the functional continuity required by enterprise users. Consequently, bespoke negotiation of exit rights remains essential to ensure the transition of structured, semantically meaningful datasets. Legal practitioners advising on SaaS contracts routinely recommend negotiating data portability terms precisely because such rights vary by vendor.[^2]

The corporation-as-code alternative offers a different value proposition. Text files and structured data formats cost nothing to store. Git repositories are free. A founder can manage corporate data in markdown or JSON, host it in their own infrastructure (or locally), back it up trivially, and refactor at will. There is no vendor dependency, no subscription fee, no uptime concerns beyond one's own systems, no mandatory interface. Privacy is straightforward: sensitive data can live in separate files with different access controls, or values can be obfuscated with simple key-value substitution. Digital signatures present some complexity, but hashing a data structure is free and public-key cryptography is open source.

One might object that this approach suits only technically sophisticated founders, not large corporations whose boards expect polished interfaces. But this objection misunderstands the model. The structured data is the backend; the interface can be whatever the audience requires. A board that expects beautifully formatted PDF resolutions with proper signature blocks receives exactly that, rendered from the authoritative data. A director signing through an established e-signature platform signs a document generated from structured records. The difference is that the PDF is derived from data rather than the data being extracted from PDFs. For the solo founder or small team, the tradeoff is compelling regardless. Paying for good technology is reasonable, but entity management platforms charge substantial fees for what a software engineer would recognize as a straightforward data management problem. The underlying "codebase" is not complex; the complexity lies in the interface and integrations, which may not justify the cost for organizations comfortable with structured text.

## Digital Minute Books and Document Management

A different category of tools addresses document organization rather than entity modeling: digital minute books, document management systems, and contract lifecycle management software. These tools organize documents, track versions, manage approvals, and automate certain workflows. They improve on filing cabinets and email attachments, but they do not fundamentally reconceive the corporation.

A digital minute book is still a minute book. Documents are the atoms of the system. The software may index document contents, extract metadata, and provide search functionality, but it does not model the corporation as a structured entity. Relationships between documents remain implicit or are expressed through folder hierarchies and naming conventions rather than through explicit data linkages.

Contract lifecycle management tools face similar limitations. They are designed to track contract status, deadlines, and approval workflows, but they treat each contract as an independent document rather than as a component of a larger corporate structure. A share purchase agreement is stored as a PDF, not as a set of structured data about share transfers that integrates with the cap table.

## Rules as Code and Computable Law

A more ambitious tradition has emerged under the banner of "Rules as Code" (RaC). Pioneered in New Zealand and gaining attention through OECD publications and academic initiatives at MIT and Stanford, RaC proposes encoding legal rules in machine-executable form alongside their natural language expression.[^3] If legislation and regulations were available as code, the reasoning goes, compliance could be automated, policy implications could be tested, and legal services could be delivered at scale.

The intuition behind RaC is sound, and its goals overlap substantially with those of this paper. Both approaches seek to make law computable. Both recognize that natural language, while essential for human understanding, is poorly suited to automated processing. Both envision a future, to us inevitable, in which legal artifacts exist in dual representations: human-readable and machine-executable.

Yet RaC faces implementation and change management challenges that corporation-as-code largely avoids. Legal rules are inherently interpretive. Statutes contain ambiguous terms, competing interpretations, and exceptions that depend on context. Encoding such rules requires resolving ambiguities that legislatures deliberately left open or that courts have not yet addressed. More significantly, rules change through complex legislative and regulatory processes. Each amendment requires updating the encoded representation, validating consistency, and managing the transition. The scale of legislative and regulatory drafting, spread across multiple jurisdictions and subject areas, makes comprehensive rules-as-code implementation a formidable undertaking.

The rise of large language models has introduced a probabilistic alternative for handling ambiguous rules, but this introduces its own complications around auditability and legal certainty.

Corporation-as-code offers a more tractable entry point. Corporate data is primarily factual, not normative. The question "who owns how many shares of what class" does not admit multiple interpretations in the way that "reasonable care" or "material adverse change" might. The capital structure of a corporation is deterministic: shares were issued or they were not; directors were appointed or they were not; filings were made or they were not.

Crucially, new businesses can adopt corporation-as-code from inception. There is no legacy conversion, no change management for existing encoded rules, no political process to navigate. A founder incorporating a company today can represent that company as structured data from the start, building the corporate record correctly rather than retrofitting it later. This fresh-start advantage makes corporation-as-code adoption fundamentally simpler than retrofitting entire legal codes into machine-executable form.

The competitive implications deserve emphasis. In some industries, legacy enterprises with document-centric infrastructure may find themselves structurally unable to compete with digital-native entrants. The operational overhead of maintaining and reconciling paper-paradigm records becomes a permanent cost disadvantage.

## The Gap

What is missing, then, is not better tools within the existing paradigms but a different paradigm altogether. Entity management platforms treat data as a backend for document generation rather than as the authoritative corporate representation. Document management systems organize documents without modeling the corporation. Rules-as-code initiatives tackle the hardest problem (normative rules) while leaving the easier problem (factual corporate data) largely unaddressed.

The corporation-as-code proposal fills this gap. It does not require solving the deep problems of legal interpretation. It requires only that we recognize what entity management platforms already know but do not operationalize: the corporation is a data structure, and documents are views over that structure. Making this explicit, and building systems that treat the data structure (not the documents) as authoritative, is the next step.

[^1]: Opara-Martins, Justice, Reza Sahandi, and Feng Tian. "Critical analysis of vendor lock-in and its impact on cloud computing migration: a business perspective." Journal of Cloud Computing 5, no. 1 (2016): 4. https://doi.org/10.1186/s13677-016-0054-z
[^2]: World Commerce & Contracting. "SaaS Contracting Guide." June 2023. https://www.worldcc.com/Portals/IACCM/SaaS%20Contracting%20Guide.pdf
[^3]: Morris, Jason. "Blawx: Rules as Code Demonstration." MIT Computational Law Report, August 14, 2020. https://law.mit.edu/pub/blawxrulesascodedemonstration/release/1
