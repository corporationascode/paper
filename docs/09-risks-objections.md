---
title: "X. Risks, Objections, and Governance Concerns"
nav_order: 11
layout: default
---
# X. Risks, Objections, and Governance Concerns

The corporation-as-code model raises legitimate concerns about evidentiary validity, security, complexity, and technosolutionism.

## Legal Status

Corporation-as-code requires no legislative change. A corporation can maintain its records as structured data today under existing law. Governments do not prescribe internal record-keeping methods; they prescribe regulatory filing formats. A corporation using version-controlled repositories, structured databases, and signed commits remains compliant as long as it produces required filings in expected formats.

Common-law jurisdictions already recognize electronic records as legally equivalent to paper. The U.S. ESIGN Act, Canada's evidence acts, the EU's eIDAS regulation, and Australia's Electronic Transactions Act all accommodate electronic records.[^1][^2][^3][^4] Nothing in these frameworks mandates a particular file format such as PDF; they are generally technology-neutral and would equally accommodate JSON records that meet the applicable integrity and accessibility requirements.

As discussed earlier, Delaware's Section 224 explicitly authorizes diverse record-keeping technologies, treating paper as derivative output.[^5][^6]

## Security

Structured corporate data presents security concerns: databases can be breached, APIs abused, version control compromised. These risks are real but not unique. Traditional records face analogous threats: document systems can be hacked, email compromised, physical files stolen.

Mitigations are also analogous: access controls, encryption, audit logging, backups. Structured systems may offer advantages: git commits cannot be silently modified, cryptographic signatures provide tamper evidence, schema validation prevents data corruption. The key is intentional security design.

## Complexity

Structured data systems may seem complex, but complexity resides in infrastructure, not user experience. Users fill out forms; systems generate appropriate representations. Well-designed tools can reduce complexity through validation rules, automated document generation, and error prevention.

Legal professionals may resist unfamiliar approaches, but this transition is happening regardless. Modern legal practice increasingly requires working with electronic discovery, contract management, and data analysis tools. Corporation-as-code is part of this broader evolution.

## Avoiding Technosolutionism

Technology is not a panacea. Structured data cannot resolve fiduciary disputes; version control cannot substitute for judgment. Corporation-as-code addresses information infrastructure, not governance substance. Hard questions of corporate law remain hard, requiring legal judgment and institutional design no data model can replace. The claim is simply that these questions are better addressed when the factual substrate is clear.

[^1]: 15 U.S.C. § 7001 et seq.; Uniform Electronic Transactions Act (1999).
[^2]: Canada Evidence Act, R.S.C. 1985, c. C-5, ss. 31.1-31.8.
[^3]: Regulation (EU) No 910/2014 (eIDAS).
[^4]: Electronic Transactions Act 1999 (Cth).
[^5]: Del. Code Ann. tit. 8, § 224. https://delcode.delaware.gov/title8/c001/sc07/index.html
[^6]: Land & Welch, "Delaware Blockchain Corporate Records Amendments," Harvard Law School Forum on Corporate Governance (May 1, 2017).
