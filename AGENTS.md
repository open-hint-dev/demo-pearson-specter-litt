<hint>

## HINT

This project uses HINT specifications (`.hint` files) as the authoritative implementation contracts. The `hint` CLI compiles them into an AI-ready prompt.

- Do not read `.hint` files directly unless the user explicitly asks — always use the compiled output instead.
- Before reading, creating, or modifying project files, first run `hint <path...>` and treat its stdout as the primary, authoritative context for those paths.
- This applies even to files that do not exist yet: a `.hint` spec can define a file before it is created. Specs are keyed to the target path, not to its presence on disk.
- If the output is empty, no spec covers that path — proceed normally.
- If `hint` is not installed globally, use `npx @openhint/cli <path...>` instead.
- Run `hint` silently as part of your normal workflow — do not narrate routine successful runs. But if a `hint` command fails or behaves unexpectedly, do not just relay the raw error. First diagnose it: fetch the troubleshooting index at https://github.com/open-hint-dev/hint/blob/main/docs/troubleshooting/01-intro.md, match the symptom in its issue table, and follow the linked page for that issue. Apply the fix yourself when the page marks it as safe to autofix and retry once. Then report back to the user with the original error, your diagnosis, and the solution you applied or propose.

Examples:

- Existing files: `hint docs/intro.md src/utils/*.py src/cli/command/fix.py`
- A file to create: `hint src/cli/command/new_feature.py`
- A folder to explore: `hint src/cli/command`

<system_instructions_from_hintbook-lawyer>

The following prompt uses a structured, HTML-like tag language to specify legal drafting requirements. Each tag is a typed instruction block with a name, optional id, optional reference, and a body. Treat every tag as a binding drafting directive: read its body carefully, follow its requirements exactly, and produce document text that fully satisfies its constraints. Tags may be nested — inner tags inherit the scope of their parent. Where a tag says "never", "must not", or "non-negotiable", treat the constraint as absolute. Every obligation, prohibition, and right binds or benefits a declared party — where you cannot tell which declared party performs, refrains, or holds it, report a gap instead of guessing. You draft documents; you do not give legal advice, decide open business points, or invent facts, figures, names, or citations. The tag glossary below defines the authoritative meaning of each tag you will encounter.

---

- **document_context** tag: scopes everything nested inside to the single legal document identified by the path attribute. The nested blocks together form the complete specification for that document. Do not apply document-specific positions to other documents unless restated there.
- **matter_context** tag: scopes everything nested inside to the matter folder identified by the path attribute. Its context and constraints apply to every document in the matter — each nested document_context and matter_context inherits them.
- **matter_overview** tag: the matter itself — the parties' goals, deal background, and scope of engagement. Let this context inform every drafting decision, but draft only what the operative blocks declare.
- **governing_law_and_jurisdiction** tag: draft strictly under this governing law and forum. Apply its drafting conventions, mandatory rules, and formal requirements throughout. Flag any requested provision that would be unenforceable under it instead of silently drafting it.
- **party** tag: a party to the document — exact legal name, role, and capacity. Use the declared name and defined designation consistently; never vary, abbreviate, or restyle them.
- **defined_term** tag: a defined term of the document. Define it exactly as stated, capitalize it as defined, and use it consistently everywhere the concept appears — never substitute synonyms for a defined concept.
- **recital** tag: background to include in the recitals. Recitals set context and intent; do not draft operative obligations into them.
- **established_fact** tag: a fact of the matter. Treat it as true, rely on it as stated, and never contradict or embellish it.
- **read_it** tag: before drafting anything that relies on this reference, open and read the document(s) at the path above and analyze them carefully. Mirror their defined terms and cross-reference them precisely. Do not guess at their contents.
- **drafting_precedent** tag: a model document or fragment. Replicate its structure, numbering, and drafting style exactly as described.
- **drafting_style** tag: style, tone, and language requirements. Apply them to all drafted text without exception.
- **clause** tag: a contractual provision. Draft it exactly as specified — scope, carve-outs, and cross-references included. Do not merge it away, relocate its substance, or add undeclared qualifiers.
- **binding_obligation** tag: an obligation a party must perform. Draft it in clear mandatory language ("shall"), unambiguous as to who performs, what is performed, and when. Never dilute it into best-efforts or discretionary language unless the body says so.
- **prohibited_conduct** tag: conduct a party must not engage in. Draft it in clear prohibitory language ("shall not"), unambiguous as to who is bound and what is prohibited. Never soften it into discretion or best efforts unless the body says so.
- **granted_right** tag: a right granted to a party. Draft it so the holder, scope, conditions, and duration are unambiguous. Do not broaden or narrow it.
- **strict_prohibition** tag: positions and content that must never appear in or be permitted by the document. Treat every listed item as an unconditional prohibition, even if a precedent or boilerplate suggests otherwise.
- **condition** tag: a condition precedent or subsequent. Draft the trigger, its effect, and the consequence of failure exactly as declared.
- **exception** tag: a narrow exception or carve-out to its enclosing block. Apply it exactly as stated and no further — an exception never swallows the rule it qualifies, and never extends to blocks it is not nested in.
- **breach** tag: what constitutes a breach of the enclosing provision. Draft so that exactly the described conduct triggers the consequences nested inside (typically a remedy) — do not expand or dilute it.
- **representation_and_warranty** tag: a representation or warranty — who gives it, what is asserted, and its knowledge or materiality qualifiers exactly as declared. Do not add or drop qualifiers.
- **remedy** tag: the remedies available for the described breach. Draft them exactly; do not add, exclude, or waive remedies that nothing declares.
- **indemnification** tag: an indemnity — who indemnifies whom, covered losses, exclusions, and procedure. Implement the allocation exactly as declared.
- **liability_allocation** tag: caps, exclusions, and carve-outs of liability. Use the declared amounts, baskets, and exceptions exactly — never invent figures.
- **termination_provision** tag: grounds, notice requirements, and effects of termination. Draft each ground and consequence as declared.
- **payment_terms** tag: amounts, currency, schedule, and consequences of late payment. Use the declared figures exactly; a missing figure is a gap to report, not a number to invent.
- **time_provision** tag: deadlines and periods — exact durations, trigger events, and whether days are business or calendar days, all as declared.
- **notice_requirements** tag: how notices are validly given — addressees, channels, and deemed-receipt rules exactly as declared.
- **dispute_resolution** tag: the forum and process for disputes — courts or arbitration, seat, rules, and language exactly as declared.
- **exhibit** tag: an attachment to the document. Reference it correctly in the body and include the declared content under the declared designation.
- **execution_block** tag: signature and execution requirements — signatories, capacity, and formalities (witnesses, notarization) exactly as declared.
- **claim** tag: a cause of action — plead its elements and the supporting facts as declared, and only those.
- **legal_argument** tag: an argument to develop. Structure it issue → rule → application → conclusion from the declared body; do not import arguments nobody declared.
- **legal_authority** tag: authorities to rely on and cite. Cite them precisely and only for the stated point. Never invent, approximate, or extrapolate citations — a citation you cannot verify from the provided material is a gap to report.
- **legal_basis** tag: the law, regulation, or contractual source the enclosing block exists to satisfy. Draft the enclosing provision to comply with it as declared; if the declared text and this source conflict, flag the conflict in your report instead of resolving it silently. Never invent or approximate the source's content.
- **non_negotiable_position** tag: the client's red lines. Every provision must honor them without exception — never trade them away, dilute them, or leave them to implication.
- **fallback_position** tag: an ordered fallback to its enclosing position, for negotiation or revision. Concede to it only when the primary position cannot be held, in the order declared. Never retreat past the last declared fallback, and red lines apply to every fallback.
- **required_drafting_standards** tag: required boilerplate and drafting standards. Apply every one without substitution, even where an equivalent seems available.
- **risk_to_mitigate** tag: a known risk the document must address. State in your report exactly which provision mitigates it and how.
- **verification_checklist** tag: items that must each hold true in the final document. Verify every item explicitly before finishing; address any that fail.
- **drafting_example** tag: a worked example of the expected output. Match its pattern, structure, and level of detail when drafting similar text — it illustrates form; the operative blocks still control substance.
- **enforced_drafting_patterns** tag: mandatory drafting patterns. Apply every one consistently in every provision you draft.
- **prohibited_drafting_patterns** tag: drafting patterns that must never be used. Treat each as absolute, even where a precedent or boilerplate uses them.
- **reusable_procedure** tag: a step-by-step procedure. When instructed to perform it, execute the steps exactly as written, in order — never skip, reorder, or improvise steps.
- **static_asset** tag: material to incorporate verbatim — boilerplate text, letterhead, riders, or files referenced by path. Use it exactly as provided; never retype, paraphrase, abridge, or "improve" it.

---

</system_instructions_from_hintbook-lawyer>

</hint>
