---
title: "IX. Interoperability, Standardization, and the Role of the State"
nav_order: 10
layout: default
---
# IX. Interoperability, Standardization, and the Role of the State

Organizations can implement corporation-as-code today using existing tools and formats. The core benefits (version control, auditability, automated document generation, machine-readable corporate history) are achievable immediately with zero dependency on external infrastructure. Government adoption of structured data APIs would enhance interoperability and reduce friction at regulatory touchpoints, but these are accelerants, not prerequisites.

## Value Independent of Infrastructure

Corporation-as-code delivers immediate benefits independent of government participation. An organization maintaining its corporate state in structured formats gains instant auditability through version control, automated document generation from canonical data, machine-readable corporate history, trivial backup and migration, and a foundation for future interoperability. The value proposition stands on its own: a founder can manage their entire corporate structure in Git with markdown and JSON files, generate all required documents programmatically, and migrate to any future standard with straightforward code.

## Government APIs as Accelerants

While not prerequisites, government APIs that expose structured corporate data amplify the benefits of corporation-as-code. Corporate data flows through government systems at critical points: incorporation, annual filings, regulatory disclosures, beneficial ownership reporting. When governments expose this information through APIs and accept filings in structured formats, they reduce compliance friction and enable ecosystem innovation.

The current state of government corporate services is uneven. The UK Companies House and SEC EDGAR provide robust APIs, while many U.S. state registries remain PDF-centric despite maintaining structured data internally. The United Kingdom's Companies House demonstrates what's possible through its comprehensive REST API exposing company data in JSON format.[^1]

## The U.S. SEC: Government-as-API at Scale

The U.S. Securities and Exchange Commission's EDGAR system demonstrates what government corporate data infrastructure can look like. The SEC provides RESTful APIs exposing filing data in JSON format, without authentication or API keys.[^3] Developers can query for complete filing histories, financial concepts across companies, and cross-company comparisons. Data updates in real-time (within seconds of filing dissemination). Bulk downloads of the entire dataset are available nightly. For public companies, the SEC has already built what corporation-as-code envisions: the question is why state registries don't provide equivalent APIs for private company records.

## Variable Progress Elsewhere

Other jurisdictions show varying degrees of progress. Corporations Canada provides XML and JSON formats for certain filings. ASIC in Australia offers API access for some registry functions. Yet many U.S. state registries remain document-first, returning PDF certificates and scanned documents rather than structured data.

## International Standards Taking Hold

Cross-border standardization is already happening through market adoption. The Legal Entity Identifier (LEI), coordinated by GLEIF and endorsed by the G20 and Financial Stability Board, provides a unique 20-character code for every legal entity in financial markets, with a free, public global directory.[^4] The Beneficial Ownership Data Standard (BODS) offers an open schema for ownership information in JSON.[^5] OASIS reports that UBL (Universal Business Language) underpins an estimated $11 billion market for standardized business document exchange and is used in over 190 countries.[^6] If invoices can be standardized globally, so can corporate filings.

In practice, entity normalization will likely evolve as a blend of shared standards and local mappings. Organizations can maintain internal IDs and schemas that fit their operational needs, while exposing translation layers (or mapping tables) that support cross-system entity resolution. This pattern is common in financial services, where firms use internal identifiers but map to LEI for external reporting, and in e-commerce, where vendors rely on internal SKUs alongside standard product identifiers.[^8]

As organizations start exposing corporate data through APIs or via MCP-style tool integrations, market incentives may encourage convergence around a small number of widely adopted identifiers and schemas. A more practical question is which conventions reach critical mass through adoption and network effects, and where plural standards persist with adapters. Where ISO identifiers already exist (e.g., LEI, country codes), they are natural coordination points for interoperability. In domains without established ISO standards, widely implemented open schemas may function as de facto standards in practice. Organizations that invest in a coherent, well-documented internal data model lower the marginal effort required to adopt emerging external standards.

## Regulatory Context: The EU Data Act

The EU Data Act (Regulation 2023/2854), effective September 2025, mandates that connected products make data available "by default, easily, securely, free of charge, in a comprehensive, structured, commonly used and machine-readable format."[^7] The regulation mandates API-based access, 30-day switching rights between service providers, and quality equivalence for exported data. While focused on connected products, the EU Data Act establishes a regulatory precedent for codifying data portability requirements. Whether such mandates prove effective will emerge over time, but they demonstrate that structured data export obligations can be formalized in law. Similar principles could hypothetically apply to corporate data held by formation services, registered agents, and entity management platforms, though market-driven adoption may obviate such requirements.

## Why Government APIs Matter

Governments serve as the authoritative source for corporate existence. When they expose structured APIs, the benefits extend in multiple directions: reduced compliance costs for businesses, automated validation for regulators, transparency for the public, and innovation platforms for the private sector. Jurisdictions that provide such infrastructure gain competitive advantages in attracting incorporations and enabling their business ecosystems.

## A Pragmatic Path Forward

The ideal end state involves corporations maintaining records as structured data, with government registries accepting filings in structured formats. But this vision does not depend on universal adoption. Organizations can implement corporation-as-code today by representing their corporate state as structured data from inception.

Even without standardized APIs across jurisdictions, a well-designed schema provides immediate benefits. A founder maintaining their corporate structure in a sound data model can convert to any eventual standard with straightforward code. The value proposition stands independent of government infrastructure, though it compounds when registries provide APIs.

The examples of jurisdictions that have embraced structured data (UK Companies House, parts of Canada and Australia) demonstrate feasibility and provide models. As more organizations adopt structured approaches, network effects will drive standardization. The practical path is to start now, with existing tools and formats, building the foundation that future interoperability will require. Waiting for universal infrastructure would be waiting indefinitely.

[^1]: UK Companies House, "API Overview," https://developer.company-information.service.gov.uk/overview/
[^3]: SEC, "EDGAR Application Programming Interfaces," https://www.sec.gov/search-filings/edgar-application-programming-interfaces
[^4]: GLEIF, "Introducing the Legal Entity Identifier (LEI)," https://www.gleif.org/en/organizational-identity/introducing-the-legal-entity-identifier-lei
[^5]: Open Ownership, "Beneficial Ownership Data Standard," https://standard.openownership.org/
[^6]: OASIS Open, https://www.oasis-open.org/
[^7]: Regulation (EU) 2023/2854 (Data Act), https://eur-lex.europa.eu/eli/reg/2023/2854/oj/eng
[^8]: ISDA and GFMA, "LEI Implementation: Industry Survey for FSB Peer Review" (October 2018), https://www.isda.org/a/brvEE/ISDA_GFMA_FSB-Peer-Review_LEI-Implementation_3-October-2018_FINAL_Public.pdf; GS1 US, "Guide to UPCs," https://www.gs1us.org/upcs-barcodes-prefixes/guide-to-upcs
