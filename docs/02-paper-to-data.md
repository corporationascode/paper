---
title: "II. From Paper Artifacts to Data Structures"
nav_order: 3
layout: default
---
# II. From Paper Artifacts to Data Structures

The document's privileged status in corporate law is not accidental. It reflects centuries of practice in which paper was the only durable, portable, and verifiable medium for recording transactions and commitments. A signed charter, a sealed certificate, a witnessed resolution: these artifacts served simultaneously as evidence, communication, and authorization. Legal formalities developed around physical objects. Signatures authenticated identity, seals indicated authority, witnesses attested to execution. When disputes arose, courts examined documents.

When digitization arrived, it preserved these conventions rather than questioning them. Electronic documents replicated the form of paper documents. Digital signatures authenticated electronic files in the same way wet signatures authenticated paper. The result was a legal system that remained conceptually organized around documents even as the underlying medium changed. The document retained its privileged status as the source of truth for corporate existence, even when the information it contained could have been represented in fundamentally different ways.

## The Limitations of Document-Based Representation

Treating documents as the authoritative representation of corporate reality imposes significant constraints. Consider what a typical corporate record contains: articles of incorporation, bylaws, board resolutions, shareholder resolutions, share certificates, option agreements, employment contracts, regulatory filings. Each document contains structured information (names, dates, amounts, conditions, relationships) encoded in prose paragraphs.

The relationships between these elements remain implicit. A share certificate describes an ownership interest, but it does not link programmatically to a shareholder record, a share class definition, or a capitalization table. These aggregate relationships (who owns what percentage, which share classes carry which rights, how ownership has changed over time) exist in the minds of lawyers and administrators, or in separate spreadsheets maintained alongside the documents, but not in the documents themselves. Extracting the corporate structure from a minute book requires reading and interpretation, not querying.

Versioning presents similar challenges. When a corporation amends its bylaws, the result is a new document (amended and restated bylaws) rather than a tracked change to a single evolving object. Understanding the history of a provision requires comparing successive documents, often manually. There is no native "diff" showing what changed between versions, no commit history recording who made changes and when, no ability to roll back to a previous state.

Every downstream use of corporate information requires extraction. Due diligence teams read documents to populate data rooms. Compliance systems parse filings to check regulatory requirements. Cap table software imports information from certificates and agreements. Each extraction introduces opportunities for error, and the same information, repeated across multiple documents, is prone to drift and inconsistency.

Document-based representations also resist interoperability. There is no standard way to exchange corporate information between systems. Each entity management platform, each law firm, each registry maintains its own formats and conventions. Moving corporate data from one system to another typically means exporting documents and re-entering information, a process that scales poorly and undermines the efficiency gains that digitization was supposed to provide.

## What Data Structures Offer

Structured data representations address these limitations directly. A data structure defines a schema in advance: fields with names and types, constraints on valid values, relationships between entities. Rather than encoding information in prose, structured data makes it explicit and queryable.

Consider how a corporation might be represented as a data structure. A core entity (call it `Corporation`) would have attributes: legal name, jurisdiction of incorporation, formation date, status, registered agent. Related entities would represent shareholders, directors, officers, share classes, and resolutions. Relationships would be explicit: a shareholder owns a specified number of shares of a particular class; a director was appointed by a resolution on a given date; a subsidiary is wholly owned by its parent.

History becomes native to the representation. Each change to the corporate structure (a share issuance, a director resignation, a bylaw amendment) is recorded as a discrete event with a timestamp, an author, and a description of what changed. The current state of the corporation is the result of applying all historical events in sequence. Any previous state can be reconstructed by replaying events up to a given point. Differences between states can be computed automatically.

Consider the analogy to a software repository. At the core is a Git-like layer: once corporate records are represented as canonical, structured data, the corporation maintains an immutable, versioned record of corporate facts. Proposed actions can be modeled as branches, changes as signed commits, and effective outcomes as merges. This layer supports diffs, provenance, and "as-of" views without embedding assumptions about users or permissions. A director resignation, for example, becomes a signed, timestamped, and attributable commit that is atomic, traceable, and replayable, rather than a document circulated by email.

On top of this record sits a governance and integration layer, analogous to a modern Git hosting platform. This layer exposes APIs, workflows, and subscriptions that allow external systems and counterparties to rely directly on the underlying facts. A lender can validate current signing authority (and any applicable limits) without requesting officer certificates. A tax advisor can query an ownership snapshot as of a specific reporting date. Counterparties can subscribe to notifications for the particular facts they depend on, for instance, officer appointments, registered address, and ownership thresholds, rather than awaiting periodic filings.

Access control lives squarely in this outer layer. Role-based access control governs who may read, propose, approve, or rely on different parts of the corporate record. A corporate secretary may have write access to board composition and read access to shareholder records; a director may have approval authority for resolutions but read-only access to cap table details; an investor's counsel may see only their client's holdings and related agreements; an auditor may receive broad but time-limited read access. External parties can be granted scoped API roles: a bank verifying corporate authority sees current officers and signing powers, and nothing else. Because permissions are expressed as data rather than embedded in document-sharing conventions, they become auditable, enforceable, and consistent across systems.

Finally, validation shifts from downstream review to input-time enforcement. Schemas can require that a share issuance reference a valid class, that a director appointment be supported by an approved resolution, or that jurisdictions be drawn from a defined set. Errors that would otherwise propagate through documents and spreadsheets are caught at the moment of entry, before they harden into the corporate record.

## Real-World Precedents

This approach is not hypothetical. Several jurisdictions and organizations have begun treating corporate information as structured data rather than document collections.

The United Kingdom's Companies House provides a REST API exposing company data in JSON format.[^1] Developers can query for company profiles, filing histories, officer appointments, and persons with significant control. The data is available programmatically, described by OpenAPI specifications, and exchangeable across any system that can consume JSON. Companies House describes JSON as "an open, standard format for storing and exchanging data" that is "easier to use than XML and more compact." This is corporate information treated as data, not documents.

Microsoft's Common Data Model offers a standardized framework for describing business entities.[^2] A model.json file defines entities with attributes (name, data type, description), relationships between entities, and metadata about data provenance and schema compliance. The pattern is directly applicable to corporate data: entities for corporations, shareholders, directors; attributes for names, dates, jurisdictions; relationships for ownership, control, appointment. If enterprise software can standardize on common data models for customers, products, and transactions, there is no principled barrier to standardizing corporate legal structures.

The U.S. Securities and Exchange Commission provides perhaps the most compelling proof of concept. Since 2018, the SEC has mandated Inline XBRL for financial filings, a format that is simultaneously human-readable and machine-readable.[^3] Rather than requiring separate documents for humans (HTML) and machines (XBRL exhibits), Inline XBRL creates "a single document that is both human-readable and machine-readable." Data is embedded directly in the filing; users can click on any tagged data point to see contextual information, citations, and accounting guidance. The SEC's EDGAR system then exposes this data through free, open REST APIs (no authentication required) with updates available in real-time as filings are disseminated.[^4]

These examples prove feasibility. What remains is extending structured approaches beyond isolated registries and financial filings to the full corporate record.

## The Document as Interface

Reconceiving the corporation as a data structure does not eliminate documents. It repositions them. Rather than serving as the authoritative source of corporate reality, documents become generated artifacts: human-readable views rendered from underlying data.

A board of directors still receives resolutions to review and approve. Shareholders still receive certificates evidencing their ownership. Regulators still receive filings in prescribed formats. Courts still examine documentary evidence. But these documents are outputs, not inputs. They are generated from the authoritative data structure, formatted for their intended audience, and reproducible in the sense that any point-in-time view can be regenerated from the versioned source. (This does not mean documents are deleted; retention policies still apply, and the version-controlled history preserves the complete audit trail of what was generated and when.) Even the most traditional board, accustomed to reviewing polished PDF resolutions with formal letterhead and proper signature blocks, can be accommodated: the data structure generates whatever view the audience requires.

This approach requires no change to existing law. Governments do not prescribe a specific technology or process for how corporations organize and maintain their internal records or how they produce regulatory filings or government mandated documents. A corporation that maintains its stock ledger as a JSON database, generates share certificates as needed, and submits filings in whatever format the registry requires is already operating within existing legal frameworks. The corporation-as-code model is a practice improvement, not a regulatory proposal.

Under this model, a PDF is analogous to a print stylesheet applied to structured data. The information exists in the data structure; the PDF is one possible rendering. Different renderings can serve different purposes: a summary for executives, a detailed record for auditors, a prescribed form for regulators.

Electronic signatures attach to data states rather than rendered pages. When a director approves a resolution, the signature authenticates a specific state of the corporate record (identifiable by a hash or commit identifier), not a particular PDF file. The audit trail shifts from tracking which documents were signed to tracking which state changes were authorized, by whom, and when.

## Transition Paths

The shift from documents to data structures need not be all-or-nothing. Organizations can begin by treating structured data as authoritative for new transactions while maintaining legacy documents as historical records. A corporation formed today could be "born digital" in the fullest sense, with its initial state recorded as structured data and documents generated as needed. Legacy documents can be indexed, linked to structured records, and progressively superseded without requiring complete conversion.

The born-digital advantage is significant. This advantage compounds over time and may create competitive pressure for adoption. Consider two companies operating under similar economic constraints. One relies on document-centric corporate records, requiring manual reconciliation, bespoke legal work, and periodic audits to answer routine governance questions. The other maintains structured records that enable automated compliance checks, instant verification of ownership and authority, and repeatable responses to diligence and regulatory inquiries.

The operational difference translates directly into administrative overhead. Document-centric systems scale by adding people, professional services, and process complexity; structured systems scale by adding, and connecting, data. In environments where margins are constrained, this difference is not cosmetic. Reducing the labor and external coordination required to maintain corporate correctness can materially affect viability, particularly as organizational complexity increases. Over time, firms with structured corporate infrastructure benefit from compounding administrative leverage that legacy systems struggle to replicate.

The goal is to make structure the default and documents the exception, reversing the current relationship in which data is extracted from documents rather than documents generated from data.

[^1]: UK Companies House, "API Overview," https://developer.company-information.service.gov.uk/overview/
[^2]: Microsoft, "Common Data Model - model.json," https://learn.microsoft.com/en-us/common-data-model/model-json
[^3]: SEC Release No. 33-10514, "Inline XBRL Filing of Tagged Data" (June 28, 2018). https://www.sec.gov/data-research/structured-data/inline-xbrl
[^4]: SEC, "EDGAR Application Programming Interfaces," https://www.sec.gov/search-filings/edgar-application-programming-interfaces
