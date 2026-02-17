---
title: "IV. The Corporation as Code"
nav_order: 5
layout: default
---
# IV. The Corporation as Code

Having surveyed the limitations of existing approaches, we now turn to the affirmative proposal: the corporation as code. This section develops the model in detail, drawing on concepts from software engineering to illustrate how corporate structures can be represented, versioned, and managed as structured data objects.

The core intuition is simple. A corporation, at any moment, exists in a particular state: it has a jurisdiction, a legal form, a set of shareholders with defined ownership interests, a board of directors, officers, bylaws, and a history of actions taken. This state changes over time through discrete events: shares are issued, directors resign, bylaws are amended, subsidiaries are formed. The challenge is to represent this evolving state in a form that is precise, auditable, interoperable, and amenable to automation.

Software engineers face analogous challenges daily. A codebase exists in a particular state at any moment and evolves through discrete changes. Version control systems like Git track every change, recording who made it, when, and why. The current state of the code is the result of applying all historical commits in sequence. Any previous state can be reconstructed. Differences between states can be computed and displayed. Multiple contributors can work on the same codebase, with systems managing conflicts and merging changes.

The corporation-as-code model applies these patterns to corporate governance.

## The Corporate Data Model

At the foundation of the model is a structured representation of the corporation. Rather than a collection of documents, the corporation is defined by a set of interrelated data entities. A minimal schema might include:

**Corporation**: The root entity, containing core attributes.
```json
{
  "id": "corp-001",
  "legal_name": "Acme Holdings Inc.",
  "jurisdiction": "Delaware",
  "formation_date": "2024-03-15",
  "status": "active",
  "registered_agent": {
    "name": "CT Corporation",
    "address": "1209 Orange Street, Wilmington, DE 19801"
  }
}
```

**Share Classes**: Definitions of the types of equity the corporation can issue.
```json
{
  "id": "class-common",
  "name": "Common Stock",
  "authorized_shares": 10000000,
  "par_value": 0.0001,
  "voting_rights": true,
  "votes_per_share": 1
}
```

**Shareholders**: Records of who owns what.
```json
{
  "id": "holder-001",
  "entity_type": "individual",
  "name": "Jane Founder",
  "holdings": [
    {
      "share_class": "class-common",
      "shares": 5000000,
      "acquisition_date": "2024-03-15",
      "acquisition_type": "founder_issuance"
    }
  ]
}
```

**Directors and Officers**: The humans who govern and operate the corporation.
```json
{
  "id": "director-001",
  "name": "Jane Founder",
  "role": "director",
  "appointed_date": "2024-03-15",
  "appointed_by": "resolution-001",
  "status": "active"
}
```

**Resolutions**: Formal corporate actions.
```json
{
  "id": "resolution-001",
  "type": "board_resolution",
  "date": "2024-03-15",
  "title": "Initial Organization",
  "actions": [
    "Adoption of bylaws",
    "Appointment of initial directors",
    "Authorization of share issuance"
  ],
  "approved_by": ["incorporator-001"],
  "status": "adopted"
}
```

This is illustrative, not prescriptive. The specific schema would vary based on jurisdiction, corporate form, and use case. The point is that these elements, which currently exist scattered across dozens of documents, can be represented as structured, interrelated data.

## Version Control for Corporate State

The real power of the model emerges when we apply version control concepts. In Git, a repository's history is a sequence of commits, each representing a discrete change. A commit contains a description of the change, a reference to the author, a timestamp, and a pointer to the repository state after the change.

Corporate state evolves similarly. Each corporate action (a share issuance, a director appointment, a bylaw amendment) can be represented as a commit to the corporate repository. The commit records what changed, who authorized it, when it occurred, and what the corporate state looked like afterward.

Consider a simple example: issuing shares to a new investor.

**Before the transaction**, the shareholder registry shows the founder holding 5,000,000 shares. The corporate record reflects the initial authorized capital and bylaws.

**The transaction** consists of a board resolution authorizing the issuance, an amendment to the share class if additional shares are authorized, the creation of a new shareholder record for the investor, and updates to the cap table.

**The commit** bundles these changes together with metadata:
```json
{
  "commit_id": "abc123",
  "timestamp": "2024-06-15T14:30:00Z",
  "author": "legal@acme.com",
  "message": "Series A financing: issue 1,000,000 shares to Venture Fund I",
  "authorization": {
    "type": "board_resolution",
    "resolution_id": "resolution-005",
    "approved_by": ["director-001", "director-002"]
  },
  "changes": [
    {"entity": "shareholders", "action": "create", "id": "holder-002"},
    {"entity": "cap_table", "action": "update"}
  ],
  "signatures": [
    {"signer": "director-001", "signature": "...", "timestamp": "..."}
  ]
}
```

This commit becomes part of the permanent corporate history. It cannot be altered without detection. The corporate state at any point in time can be reconstructed by replaying commits. Differences between states can be computed automatically, showing exactly what changed and when.

## Complex Structures: A Multi-Jurisdictional Example

The benefits of corporation-as-code become most apparent in complex corporate structures. Consider a holding company with subsidiaries across multiple jurisdictions: a Delaware parent, a UK operating subsidiary, a Canadian subsidiary, and a Singapore entity. The group's general counsel serves as a director on all four boards.

When the general counsel resigns, the traditional document-centric approach requires:

- Drafting resignation letters for each entity (four documents)
- Preparing board resolutions accepting the resignation (four documents, each following jurisdiction-specific conventions)
- Updating the minute books of each entity
- Filing notifications with each relevant registry (Delaware Division of Corporations, UK Companies House, Corporations Canada, ACRA in Singapore)
- Updating internal records, cap tables, and organizational charts
- Coordinating signature collection across potentially different time zones

Each step requires a lawyer familiar with the specific jurisdiction's requirements. The work is repetitive but not identical; each jurisdiction has its own forms, filing deadlines, and procedural requirements. Mistakes propagate. If the resignation date is recorded inconsistently across entities, the discrepancy may surface months later during due diligence.

In a corporation-as-code model, the same transaction becomes a programmatic operation. The corporate group is represented as a connected data structure:

```python
# Representation of a corporate group
corporate_group = {
    "parent": {"id": "acme-delaware", "jurisdiction": "Delaware"},
    "subsidiaries": [
        {"id": "acme-uk", "jurisdiction": "UK", "parent_id": "acme-delaware"},
        {"id": "acme-canada", "jurisdiction": "Canada", "parent_id": "acme-delaware"},
        {"id": "acme-singapore", "jurisdiction": "Singapore", "parent_id": "acme-delaware"}
    ]
}

# The director serves on all boards
director = {
    "id": "director-gc-001",
    "name": "Jane Doe",
    "role": "director",
    "appointments": [
        {"entity_id": "acme-delaware", "appointed": "2022-01-15"},
        {"entity_id": "acme-uk", "appointed": "2022-02-01"},
        {"entity_id": "acme-canada", "appointed": "2022-02-15"},
        {"entity_id": "acme-singapore", "appointed": "2022-03-01"}
    ]
}
```

The resignation can be effectuated with a script that iterates across the corporate structure:

```python
def resign_director_from_group(director_id, resignation_date, reason):
    """
    Resign a director from all entities in the corporate group.
    Returns a transaction bundle for review and approval.
    """
    director = get_director(director_id)
    transaction = TransactionBundle(
        description=f"Resignation of {director.name} from all group entities",
        effective_date=resignation_date
    )

    for appointment in director.active_appointments:
        entity = get_entity(appointment.entity_id)

        # Create resignation record and end the appointment
        resignation = DirectorResignation(
            director=director_id,
            entity_id=entity.id,
            effective_date=resignation_date,
            reason=reason
        )

        # Generate jurisdiction-appropriate resolution
        resolution = generate_resolution(
            entity=entity,
            action_type="accept_director_resignation",
            parameters=resignation,
            template=get_template(entity.jurisdiction, "director_resignation")
        )

        # Queue registry filing
        filing = generate_filing(
            registry=get_registry(entity.jurisdiction),
            filing_type="director_change",
            entity=entity,
            change=resignation
        )

        # Adds artifacts and updates appointment end_date atomically
        transaction.add(resignation, resolution, filing)

    # Validate the transaction
    validation_results = validate_transaction(transaction)
    if validation_results.has_errors():
        raise ValidationError(validation_results.errors)

    return transaction
```

The script generates all required artifacts: resignation records, board resolutions formatted for each jurisdiction, and registry filings in the appropriate formats. The lawyer reviews the transaction bundle, verifies that the generated documents are correct, and approves. Upon approval, the corporate state updates atomically. Where possible, filings are submitted to each registry programmatically (or queued for submission where APIs are not available).

The advantages compound with complexity. Adding a fifth subsidiary requires no additional logic; the script handles it automatically. Changing the resignation date requires updating a single parameter, not coordinating across four sets of documents. Validation rules catch inconsistencies before they propagate. The audit trail shows exactly what changed across all entities, who approved it, and when.

## Signatures and Authorization

A critical question arises: how do electronic signatures fit into this model? In the document-centric paradigm, signatures attach to documents. A director signs a PDF resolution. A shareholder signs a stock purchase agreement. The signed document is evidence of authorization.

In the corporation-as-code model, signatures attach to data states. When a director approves a transaction, they sign a cryptographic hash of the commit or the resulting corporate state. This signature attests that the director authorized the specific changes recorded in the commit.

The advantages are significant. A signature on a data state is more precise than a signature on a rendered document. The signed object is unambiguous: it is the exact data structure, not a particular visual rendering. The signature can be verified programmatically. Multiple signers can sign the same state without needing to coordinate document versions.

Traditional documents remain available as needed. A board resolution can be rendered from the data structure and signed if required for filing or litigation. But the document is a derivative artifact, not the authoritative record. The authoritative record is the signed commit.

## Prior Art and Influences

The corporation-as-code concept builds on several intellectual traditions and existing infrastructure.

The Legal Entity Identifier (LEI) system, coordinated by the Global Legal Entity Identifier Foundation (GLEIF), demonstrates that global corporate identification is achievable.[^3] Every LEI is a 20-character alphanumeric code based on ISO 17442 that uniquely identifies legal entities participating in financial transactions. The Global LEI Index is a free, public directory connecting each identifier to reference data including ownership structure: "who is who" and "who owns whom." Endorsed by the G20 and Financial Stability Board, the LEI proves that standardized corporate data can work across jurisdictions.

The Beneficial Ownership Data Standard (BODS), developed by Open Ownership, provides an open schema for publishing beneficial ownership information as structured, interoperable data.[^4] BODS defines how to represent entities, natural persons, and the relationships between them (shareholding, voting rights, board appointments, trust arrangements). The standard uses JSON, supports historical data (not just current state), and is already being adopted by multiple governments. BODS demonstrates that the hard design work of modeling corporate ownership as structured data has already been done.

The CommonAccord project, active since the early 2010s, pioneered the treatment of legal documents as "files in folders shared on GitHub."[^1] CommonAccord stores legal templates and agreements as text files in git repositories, enabling version control, collaboration, and automation. While focused primarily on contracts rather than corporate structures, CommonAccord demonstrates that git-based workflows can apply to legal artifacts.

Corporation-as-code naturally extends to certain categories of contracts, particularly those that are essentially statements of corporate fact. Consider intercompany intellectual property licenses within a corporate group: Entity X of the group is authorized to use trademark Y in jurisdiction Z. This is a contract in legal form, but its substance is a factual relationship between corporate entities and intellectual property rights. Missing or incorrect IP licenses can create significant problems (trademark ownership disputes, tax complications, liability gaps). When such licenses are tracked as structured relationships within the corporate data model, queries like "which entities are licensed to use which marks in which territories?" become trivial. The contract generates from the data; the data is authoritative.

With apologies for the self-citation, one of this paper's co-authors discussed the parallel between legal drafting and software development in 2017, arguing that "drafting a contract is very much like 'programming' the relationship between the parties" and predicting that "GitHub-like workflows will be a mainstay of at least some types of legal practices."[^5] Corporation-as-code extends this intuition from contract drafting to corporate structure itself.

Stanford's Computable Contracts Initiative has developed methods for representing contract terms as "highly structured data" amenable to automated processing.[^2] The insight that contracts can be computable extends naturally to corporate governance: if contract terms can be structured data, so can bylaws, resolutions, and capitalization tables.

The distributed systems community has explored similar patterns. Append-only logs and event sourcing (recording state changes as a sequence of events rather than overwriting current state) are established techniques for building auditable, reproducible systems. The corporation-as-code model applies these patterns to the legal domain.

Together, these influences suggest a layered architecture: LEI provides the unique identifier, BODS provides the ownership schema, and corporation-as-code extends the model to governance, history, and operations.

## What This Is Not

To avoid confusion, we should clarify what the corporation-as-code model does not claim.

It does not claim that corporations should execute themselves automatically. The corporation remains a legal fiction, enforced by courts and regulators, governed by humans exercising judgment. The model concerns representation, not execution. How the corporation is modeled and documented is distinct from how it makes decisions.

It does not claim that all corporate information can be perfectly structured. Some corporate artifacts (contracts with third parties, litigation files, informal communications) will remain unstructured or semi-structured. The model proposes that core governance elements (ownership, governance, formal actions) should be structured, not that every corporate document must be.

It does not require blockchain or cryptocurrency. While distributed ledgers offer one possible infrastructure for maintaining corporate records, the model is infrastructure-agnostic. A git repository hosted on private servers, a database with audit logging, or a public blockchain could each theoretically serve as the backend. The choice is an implementation detail, not a definitional feature.

The next section distinguishes the corporation-as-code model from a related but distinct concept: the decentralized autonomous organization.

[^1]: CommonAccord, https://www.commonaccord.org/
[^2]: Stanford CodeX, "Computable Contracts Initiative," https://law.stanford.edu/codex-the-stanford-center-for-legal-informatics/projects/stanford-computable-contracts-initiative/
[^3]: GLEIF, "Introducing the Legal Entity Identifier (LEI)," https://www.gleif.org/en/organizational-identity/introducing-the-legal-entity-identifier-lei
[^4]: Open Ownership, "Beneficial Ownership Data Standard," https://standard.openownership.org/
[^5]: Beauchamp-Tremblay, Xavier. "GitHub Workflow and Legal Drafting." Slaw, April 21, 2017. https://www.slaw.ca/2017/04/21/github-workflow-and-legal-drafting/
