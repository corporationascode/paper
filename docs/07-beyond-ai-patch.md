---
title: "VIII. Beyond AI as a Patch: Determinism, Structure, and Legal Certainty"
nav_order: 9
layout: default
---
# VIII. Beyond AI as a Patch: Determinism, Structure, and Legal Certainty

The legal industry has embraced artificial intelligence with considerable and appropriate enthusiasm. Large language models can review contracts, summarize documents, draft correspondence, and answer legal research questions with impressive fluency. AI-powered due diligence tools can process thousands of documents in seconds or minutes. Contract analysis platforms extract key terms and flag risks at scale. These capabilities are genuinely valuable, and the technology continues to improve.

The temptation, then, is to view AI as the solution to the problems described in this paper: if corporate documents are unstructured, use models to interpret them. Upload the minute book to a language model. Ask it questions. Let the AI extract the cap table, identify the current directors, summarize the board resolutions.

For the specific problem of corporate data, this approach is a Rube Goldberg machine: an elaborate workaround for a problem that admits a simpler solution.

## The Efficiency Illusion

Consider what happens when an organization uses AI to manage unstructured corporate records. The minute book is a collection of PDFs. The cap table is a spreadsheet that may or may not match the stock purchase agreements. The board resolutions are scattered across email attachments and document management systems. To answer a simple question ("How many shares does Investor X hold?"), the AI must:

1. Identify which documents might contain the answer
2. Parse the documents (handling varied formats, scanned images, inconsistent naming)
3. Extract the relevant information
4. Reconcile conflicts between sources
5. Present an answer with appropriate caveats

This works, more or less. Modern AI systems are remarkably capable at document interpretation. Hallucination risks, while not eliminated, have diminished substantially for sophisticated tools that ground responses in source documents. The outputs require verification, but a well designed process absolutely saves time compared to manual review.

Yet practitioners at the frontier of AI-powered document analysis report that the challenges are worse than they first appear. Foundation-model capability is no longer the main bottleneck for extraction. With tuned prompts, the right model choice, and a well-designed retrieval pipeline, 92%+ accuracy is already being delivered, and performance improves as models and retrieval quality advance.[^24] The complexity comes from handling long-tail prompting edge cases to reach higher accuracy, and from operating reliably under degraded or adversarial document conditions. Virtual data rooms, e-signature platforms, and other systems increasingly deploy encryption, watermarking, and obfuscation techniques that actively prevent AI analysis. Parsing such documents requires complex parsing pipelines to handle handwritten annotations, table structure extraction, visual overlays (such as watermarks), and other obfuscating artifacts, and to contend with restricted or encrypted files when access is authorized. These pipelines typically become more complex and costly as these techniques become more sophisticated.

Even when documents are accessible, the interpretive work does not disappear; it is encoded into prompting infrastructure. Consider the task of classifying the distribution waterfall structure from a limited partnership agreement. Hybrid structures often blur the line between "American" and "European" distribution mechanics, forcing practitioners to make judgment calls about classification. If you want to turn legal documents into data primitives, you must map this interpretive process into a system that can consistently process variations across thousands of documents. The work is possible but hard, expensive, and inherently subjective at the margins.

Most "hallucinations" in sophisticated production systems are not model hallucinations in the technical sense. They are prompt-specification issues, including prompt-induced bias and instructions that appear unambiguous yet leave edge-case behavior underconstrained.

The problem, then, is not that AI fails. The problem is that the entire exercise is unnecessary overhead. We are deploying expensive computational resources to recover structure that should have been present from the start. We are asking AI to clean up a mess rather than preventing the mess.

## Why the Patch Is Costly

Using AI to interpret unstructured corporate data imposes several costs beyond the obvious computational expense:

**Data spreads rather than consolidates.** Each AI tool maintains its own index, its own cache, its own interpretation of the source documents. The corporate data that should live in one authoritative place instead exists in fragments across multiple vendor systems. Switching tools means re-ingesting documents and hoping for consistent interpretation. Worse, model deprecations and updates can change behavior in previously stable extraction pipelines. Organizations therefore incur ongoing costs not only to build these systems, but to continuously monitor, validate, and re-tune them as models evolve, costs that scale poorly with adoption.

**The underlying mess persists.** AI interpretation does not fix bad data; it routes around it. The minute book remains disorganized. The cap table spreadsheet remains out of sync with the legal documents. The next time someone needs to answer a corporate governance question, they face the same unstructured mess, perhaps with a different AI tool that interprets it slightly differently.

**Verification overhead remains.** For consequential decisions (financing rounds, M&A due diligence, regulatory filings), professionals must verify AI outputs against source documents. The AI provides a first pass, but human review catches the cases where interpretation went wrong. This is appropriate caution, but it means the efficiency gains are smaller than they first appear.

**Bad habits compound.** When AI makes unstructured data tolerable, the incentive to structure data properly diminishes. Organizations continue generating documents in formats that require interpretation rather than formats that encode information directly. The problem perpetuates itself.

**Compliance burden multiplies.** The costs extend beyond technical infrastructure. Rothmann (2025), proposing "Company as Code" as a structured representation of organizational policies and operations, describes spending hundreds of person-hours collecting evidence and updating documentation for ISO 27001 audits, work that could have been invested in product development.[^27] While Rothmann focuses on the organizational layer (people, roles, operational policies), the compliance overhead he identifies applies equally to the legal entity foundation we address. With policy-as-code and structured organizational data, auditors could query the organizational model directly, with traceable mappings from policy statements to implementation evidence, rather than requiring manual evidence gathering for each audit cycle. The overhead of maintaining dual representations (operational reality in systems, compliance documentation in documents) compounds as regulatory requirements expand.

## Determinism and Legal Certainty

Legal systems value certainty. Property rights, contract enforcement, and corporate governance depend on clear answers to deterministic questions. Ambiguity exists in law (what constitutes "reasonable" behavior, whether a contract term is enforceable), but much corporate information is not inherently ambiguous. The capital structure of a corporation is deterministic and objective. The identity of directors is deterministic. The filing history with state regulators is deterministic.

These deterministic elements should be represented in ways that yield consistent answers when queried. A structured database returns the same result for the same query. A JSON schema either validates or fails. A git commit history shows exactly what changed and when. There is no interpretation, no probability, no hallucination risk.

The corporation-as-code model achieves this determinism by design. Corporate state is structured data. Queries return deterministic answers, not interpretations. Changes are logged immutably. The history is complete and auditable.

This does not eliminate all ambiguity from corporate law. Interpretive questions remain: What does a bylaw provision mean? Did a board act within its authority? Is a transaction fair to minority shareholders? These questions require human judgment and may ultimately require court resolution. But the deterministic substrate on which these questions depend (who owned what, what was authorized, what was disclosed) should not itself be a source of uncertainty.

## AI as Operator, Not Interpreter

The appropriate role for AI in corporation-as-code is not as interpreter of unstructured documents but as operator on structured data.

An AI agent managing a corporate repository does not read PDFs and guess at their meaning. It queries structured records, validates inputs against schemas, generates documents from templates, and triggers workflows based on defined rules. When it encounters ambiguity (a missing field, a constraint violation, an unusual request), it escalates to humans rather than guessing.

This is a fundamentally different posture. The AI operates within a deterministic framework, performing tasks that are well-defined and verifiable. Its outputs can be checked against schemas. Its actions can be audited. Its errors are detectable.

The contrast with AI-as-interpreter is stark. An AI reading unstructured corporate records to extract a cap table is performing a task prone to hallucination, difficult to verify, and expensive to correct when wrong. An AI generating a cap table report from structured shareholder records is performing a task that is deterministic, trivially verifiable, and essentially error-free.

## Generative AI as the Lawyer's Programming Interface

A persistent objection to data-centric legal infrastructure has been accessibility: lawyers are not programmers, and asking them to write scripts or query databases seemed unrealistic. This objection has dissolved with the emergence of generative AI coding assistants.

Large language models trained on code can translate natural language instructions into working programs. What has been coined as "vibe coding" in February 2025[^25] is increasingly delivering real production-ready results in late 2025 and is rapidly embraced by the legal profession.[^26] A lawyer who cannot write Python can nonetheless describe what they want to accomplish: "Resign Jane Doe from all boards in the corporate group effective March 15, generate the resolutions for each jurisdiction, and queue the registry filings." The AI assistant generates the script, explains what it does, and executes it upon approval.

This capability transforms the relationship between lawyers and structured corporate data. Not all lawyers in the team need to understand the underlying data schema in detail. They describe the business outcome; the AI translates that description into operations on the corporate repository. The lawyer reviews the proposed changes, verifies the generated documents, and approves.

Consider a concrete workflow. A partner at a law firm needs to effectuate a complex reorganization: transferring ownership of a subsidiary from one holding company to another, updating director appointments, and amending intercompany agreements. In a document-centric world, this requires drafting dozens of documents, coordinating signatures, and manually updating records.

With corporation-as-code and a generative AI assistant, the workflow becomes:

1. **Describe the transaction**: The lawyer explains the reorganization in natural language, specifying the entities involved, the effective date, and the business objectives.

2. **Generate the script**: The AI produces a script that queries the corporate repository, identifies affected entities and relationships, generates the required changes, and produces the necessary documents (transfer agreements, board resolutions, amended shareholder registers).

3. **Generate validation tests**: Critically, the AI also generates tests to verify that the resulting corporate structure is valid. These tests check invariants: Does every subsidiary have a parent? Do ownership percentages sum to 100%? Are all required officers appointed? Do intercompany agreements reference entities that still exist in their stated relationships?

```python
def test_reorganization_validity(corporate_group, transaction):
    """
    Validate the corporate structure after the proposed reorganization.
    Uses transaction.effective_date as the reference point.
    """
    errors = []
    effective = transaction.effective_date

    # Test: Every subsidiary must reference a valid parent
    for entity in corporate_group.subsidiaries:
        parent = get_entity(entity.parent_id)
        if parent is None:
            errors.append(f"{entity.name} references non-existent parent")

    # Test: Ownership percentages must sum to 100% (simplified; assumes
    # single class, no treasury shares, fully paid)
    for entity in corporate_group.all_entities:
        total_ownership = sum(s.percentage for s in entity.shareholders)
        if not is_close(total_ownership, 100.0):
            errors.append(f"{entity.name} ownership sums to {total_ownership}%")

    # Test: All directors must have valid appointments as of effective date
    for director in corporate_group.all_directors:
        for appointment in director.appointments:
            entity = get_entity(appointment.entity_id)
            if entity is None:
                errors.append(f"{director.name} appointed to non-existent entity")
            if appointment.end_date and appointment.end_date < effective:
                if director.status == "active":
                    errors.append(f"{director.name} marked active but appointment expired")

    # Test: Intercompany agreements reference valid parties
    for agreement in corporate_group.intercompany_agreements:
        for party_id in agreement.party_ids:
            if get_entity(party_id) is None:
                errors.append(f"Agreement {agreement.id} references non-existent party")

    return ValidationResult(errors=errors, passed=len(errors) == 0)
```

4. **Review and approve**: The lawyer reviews the generated script, the proposed changes, and the validation results. The proposed changes are presented as a DIFF report that precisely enumerates the intended edits to the corporate data structure, identifying affected entities, modified relationships, and value-level changes. This DIFF enables the lawyer to verify intent without reading or understanding the underlying script. The AI assistant can explain any aspect of the script in plain language on request. If the tests pass, the DIFF is correct, and the source documents are accurate, the lawyer approves and the transaction is committed atomically to the corporate repository.

5. **Generate instruments**: The system renders the authoritative data changes as traditional legal instruments: signed resolutions, transfer agreements, updated share certificates. These documents are generated from the structured data, ensuring consistency. They serve as the human-readable record of actions whose authoritative representation is the underlying data.

This workflow was difficult to imagine even five years ago. Lawyers interacting with data structures through natural language, generating custom scripts for complex transactions, and producing validated corporate changes: this required either programming expertise or expensive custom software development. Generative AI coding assistants have democratized access to programmatic corporate operations.

The implications are significant. Lawyers can now work with structured corporate data without becoming programmers. They can describe transactions in the language they already use and receive working implementations. They can generate tests that verify their work, catching errors before they propagate. The barrier between legal expertise and technical implementation has become permeable.

Furthermore, these scripts become reusable templates. A complex reorganization script, once generated and validated, can be parameterized and saved as a "corporate action" or "agent" template with input variables: director name, effective date, consideration amount, target entity. The next similar transaction requires only specifying these variables rather than describing the transaction from scratch. Law firms and corporate legal departments can build libraries of validated transaction templates, each representing accumulated expertise about how to execute particular corporate actions correctly. A "director resignation across corporate group" agent, a "subsidiary formation" agent, a "series financing" agent: these become standardized, tested, reusable components that encode best practices and reduce the risk of procedural error.

## Structure Before Intelligence

The argument is not that AI is bad, far from it. The argument is that structure should precede intelligence. The first step is representing corporate information in structured form. The second step is deploying AI to operate on that structure.

Inverting this order (deploying AI to interpret unstructured information) is an inefficient detour. It introduces risk where none is necessary. It consumes computational resources to recover information that could have been explicit. It places the burden of verification on humans who might otherwise trust the system.

Corporation-as-code gets the order right. Structure the data. Then deploy agents to maintain, query, and act on that data. The result is AI that enhances certainty rather than undermining it.

[^24]: OpenAI, "Hebbia's Deep Research Automates 90% of Finance and Legal Work, Powered by OpenAI," https://openai.com/index/hebbia/
[^25]: Andrej Karpathy (@karpathy), X/Twitter post, February 2025, https://x.com/karpathy/status/1886192184808149383
[^26]: Richard Tromans, "Jamie Tso Interview: Vibe-Coding Your Own Legal AI Tools," Artificial Lawyer, January 5, 2026, https://www.artificiallawyer.com/2026/01/05/jamie-tso-interview-vibe-coding-your-own-legal-ai-tools/

[^27]: Rothmann, Daniel, "Company as Code," 42 Futures, February 25, 2025, https://blog.42futures.com/p/company-as-code
