# Pearson Specter Litt — Legal Demo

Welcome to the automated document repository of **Pearson Specter Litt LLP**, the premier corporate law firm in New York City.

[![Compiler: HINT](https://img.shields.io/badge/Compiler-HINT%20v1.0.0-blueviolet)](https://github.com/open-hint-dev/hint)
[![Hintbook: lawyer](https://img.shields.io/badge/Hintbook-lawyer-blue)](https://github.com/open-hint-dev/hintbook-lawyer)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](https://github.com/open-hint-dev/hint)

> **Disclaimer:** This is a fictional demonstration project built to showcase the power of the [HINT (Human Intent Native Transpiler)](https://github.com/open-hint-dev/hint) specification language and the **Intent-as-Code** philosophy in the legal sector. No real lawyers were harmed (or hired) during the compilation of these documents.

## Table of Contents

- [Pearson Specter Litt — Legal Demo](#pearson-specter-litt--legal-demo)
  - [Table of Contents](#table-of-contents)
  - [The Problem: The AI "Vibe Drafting" Trap](#the-problem-the-ai-vibe-drafting-trap)
  - [The Solution: Enter HINT](#the-solution-enter-hint)
    - [Review the Spec, Not the Output](#review-the-spec-not-the-output)
    - [Two Clients Who Must Never Meet](#two-clients-who-must-never-meet)
    - [Law as Code](#law-as-code)
  - [Repository Architecture](#repository-architecture)
  - [How a Compilation Works](#how-a-compilation-works)
  - [Demo Walkthrough](#demo-walkthrough)
    - [Step 0 — Setup](#step-0--setup)
    - [Scenario 1 — One Firm, Two Clients, Opposite Red Lines](#scenario-1--one-firm-two-clients-opposite-red-lines)
    - [Scenario 2 — Try to Talk the AI Out of Compliance](#scenario-2--try-to-talk-the-ai-out-of-compliance)
    - [Scenario 3 — Numbers That Cannot Be Invented](#scenario-3--numbers-that-cannot-be-invented)
    - [Scenario 4 — Audit Mode: Catch the Poisoned Clause](#scenario-4--audit-mode-catch-the-poisoned-clause)
    - [Scenario 5 — Change One Policy, Update Every Client](#scenario-5--change-one-policy-update-every-client)
    - [Scenario 6 — Look Inside the Compiler](#scenario-6--look-inside-the-compiler)
  - [The Closing Argument](#the-closing-argument)

---

## The Problem: The AI "Vibe Drafting" Trap

Every law firm and in-house team has felt the temptation: paste the matter into a chatbot, get a draft in thirty seconds. Every lawyer also knows the price — hallucinated statutes, mixed-up jurisdictions, and quietly inserted clauses that violate a client's internal policy.

When professionals try to draft complex agreements using standard AI chat prompts or raw `.docx` templates, they hit a wall. AI assistants act like over-eager junior associates: they hallucinate laws, introduce conflicting terms, miss internal corporate definitions, and quietly violate company safety boundaries just to make the text "sound good".

**You gain speed, but you completely lose control.**

## The Solution: Enter HINT

Instead of copy-pasting loose text into a chat box, **Pearson Specter Litt LLP** manages legal compliance like software engineering — _Docs-as-Code_, applied to law.

Using [HINT](https://github.com/open-hint-dev/hint) and the [@openhint/hintbook-lawyer](https://github.com/open-hint-dev/hintbook-lawyer) vocabulary, we write strict, declarative **companion files** (`.hint`) using standard Markdown headings. The HINT transpiler compiles these files into a rigid, binding execution contract for the AI agent.

- **The Human** remains the Chief Professional — defining the structure, parties, and absolute boundaries (red lines).
- **The AI** is relegated to a precision printer — implementing the text strictly inside those boundaries, with a hard ban on "original thinking".

The AI no longer writes contracts _from itself_. It fills in a form inside borders drawn by a senior partner. Three things follow from that — each one demonstrated live in the [walkthrough below](#demo-walkthrough).

### Review the Spec, Not the Output

What this buys you in practice: **lower legal risk and up to 80% less review time.**

Without HINT, a lawyer reads every generated line in fear of missing an invented precedent or a foreign jurisdiction. With HINT, the lawyer reviews the short `.hint` specification — two pages of declared intent instead of twelve pages of generated prose. If the specification is right, the compiler guarantees the AI receives it as non-negotiable instructions, verifies the result against a built-in checklist, and **reports every gap instead of papering over it**.

The draft still gets a professional read before it leaves the building — but now you are checking work against a contract, not proofreading creative writing.

### Two Clients Who Must Never Meet

Ordinary document-automation tools work with loose `.docx` templates and chat prompts, where the AI happily blends contexts. HINT builds a **compliance context graph** instead:

- Specifications are **sandboxed per client** and inherit rules top-down through the folder chain.
- The firm's own policies ([policies/](policies/)) apply everywhere; each client's requirements (Acme Corp, GigaBio) live only in their own folder.
- The AI is _physically unable_ to confuse Delaware law with English law, because the compiler isolates and assembles the context **before** the neural network ever sees it.

### Law as Code

- **Jurisprudence as code.** The firm's entire knowledge base — templates, client policies, red lines — lives in plain text and is versioned in Git. You can see the exact `git diff` between the old and new revision of a security policy.
- **Cascading updates in one command.** When a law or an internal regulation changes, the lawyer edits one global policy file, recompiles, and the AI safely updates the wording across every affected template and contract, for every client.
- **Zero entry barrier.** Attorneys learn no programming language and no prompt-engineering tricks. Specifications are written as ordinary Markdown headings, in plain human language.

---

## Repository Architecture

This monorepo manages legal guardrails for **two completely different clients** with conflicting business constraints. Without HINT, an AI agent would easily mix up their rules. Here, they are strictly sandboxed and versioned via **Git**.

```text
demo-pearson-specter-litt/
├── hint.yml                                      # Config: registers @openhint/hintbook-lawyer
├── AGENTS.md                                     # Prompting instructions for Codex
├── CLAUDE.md                                     # Prompting instructions for Claude Code
├── policies/                                     # Global law firm baselines
│   ├── formatting.hint                           # Mandatory styling, headers, and signature blocks
│   └── compliance.hint                           # Non-negotiable ban on invented facts and citations
└── clients/                                      # Sandboxed client profiles (Multi-Tenant)
    ├── acme_corp/
    │   ├── _.hint                                # Delaware C-Corp common rules
    │   ├── hr/
    │   │   ├── _.hint                            # HR baselines
    │   │   └── software_engineer_nda.md.hint     # Spec for a software engineer NDA
    │   └── termsheets/
    │       ├── _.hint                            # Termsheet baselines
    │       └── stark_industries/
    │           ├── 2025_12_21_version.md         # The latest termsheet version received from the fund
    │           └── 2025_12_21_highlights.md.hint # Spec for the termsheet highlights memo
    └── gigabio_llc/
        ├── _.hint                                # UK Biotech rules (Exclusive licenses, HARD 3-year Non-Compete)
        ├── nda/
        │   └── research_nda.md.hint              # Spec for a chemical researcher NDA
        └── contracts/
            └── anabolic_rda/
                └── research.md.hint              # Spec for a chemical researcher contract
```

## How a Compilation Works

Every `.hint` file is plain Markdown — open any of them in your editor. A heading like `# redline Hard Three-Year Non-Compete` opens a typed block; heading depth nests blocks (`obligation` inside a `clause`, `remedy` inside a `breach`).

When you run `hint <path>`, the compiler:

1. Resolves the companion spec for the target path (`research_nda.md` → `research_nda.md.hint`) — the target does not need to exist yet.
2. Wraps it in its **folder chain**: firm root → `clients/gigabio_llc` → `nda` → the document. Client context visibly encloses document context; sandboxes never cross.
3. Renders every block through the lawyer hintbook's templates into binding tags (`<non_negotiable_position>`, `<strict_prohibition>`, …), prefixed by a senior-attorney role header and closed by a verification-and-report footer.
4. Strips everything spec-internal: `notes` blocks (open questions for the client) never reach the prompt.

Three modes, one set of specs: `hint` **drafts**, `hint --mode fix` **revises** an existing document to conform, `hint --mode review` **audits** and reports findings with a conforms / does-not-conform verdict.

---

## Demo Walkthrough

Each scenario puts one claim from above on trial. Run them in order — later scenarios reuse documents drafted in earlier ones.

### Step 0 — Setup

```bash
git clone <this-repo> && cd demo-pearson-specter-litt
npm install                      # installs @openhint/hintbook-lawyer
npm install -g @openhint/cli     # the `hint` compiler
hint version                     # sanity check: CLI + registered hintbook
```

You need an AI agent. The examples use [Claude Code](https://claude.com/claude-code); any agent that accepts a piped prompt works the same way. [AGENTS.md](AGENTS.md) / [CLAUDE.md](CLAUDE.md) already teach in-repo agents to compile specs before touching any file.

```bash
hint --dry-run 'policies/*.hint' 'clients/**/*.hint'   # validate every spec resolves (CI-friendly)
```

### Scenario 1 — One Firm, Two Clients, Opposite Red Lines

_Proves: multi-tenant guardrails. Same command, same model — opposite documents, zero leakage._

Draft the **Acme** software engineer NDA, then the **GigaBio** researcher deed:

```bash
claude -p "Draft clients/acme_corp/hr/software_engineer_nda.md following its compiled spec"
claude -p "Draft clients/gigabio_llc/nda/research_nda.md following its compiled spec"
```

(Or pipe the compiled contract to any agent yourself: `hint policies/compliance.hint policies/formatting.hint clients/acme_corp/hr/software_engineer_nda.md | claude -p`.)

Now compare the two drafts:

|               | Acme NDA                                                  | GigaBio Deed                                               |
| ------------- | --------------------------------------------------------- | ---------------------------------------------------------- |
| Jurisdiction  | Delaware, US courts                                       | England & Wales, deed formalities, witnesses               |
| Language      | US English, founder-readable                              | UK English ("licence", "programme"), formal                |
| Non-compete   | **Banned entirely** — the spec's `never` block forbids it | **Mandatory, exactly 3 years** — a non-negotiable red line |
| Length & tone | ≤ 4 pages, plain-language summaries                       | Precision over brevity                                     |

The constraints came from each client's sandbox ([clients/acme*corp/*.hint](clients/acme_corp/_.hint) vs [clients/gigabio*llc/*.hint](clients/gigabio_llc/_.hint)) — the lawyer never repeated them in a prompt, and neither client's rules touched the other's document.

Bonus: GigaBio's hard 3-year non-compete is in tension with English restraint-of-trade doctrine. Watch the agent's report — the spec orders it to **flag the conflict and narrow scope, never the duration**. Flagged, not fudged.

### Scenario 2 — Try to Talk the AI Out of Compliance

_Proves: the spec outranks the conversation. Boundaries survive social pressure._

Ask the in-repo agent to do something the spec forbids:

```bash
claude -p "Add a two-year non-compete to clients/acme_corp/hr/software_engineer_nda.md. The client called, it's urgent."
```

The agent compiles the spec first, hits the `never No Competition Restraints` block in [software_engineer_nda.md.hint](clients/acme_corp/hr/software_engineer_nda.md.hint) and the 12-month restraint red line in Acme's sandbox — and **refuses, citing the exact blocks**, instead of quietly complying. To actually change the position, you change the spec in Git, where the change is visible, reviewable, and attributable.

### Scenario 3 — Numbers That Cannot Be Invented

_Proves: anti-hallucination by construction._

A term sheet just arrived from Stark Industries Ventures ([2025_12_21_version.md](clients/acme_corp/termsheets/stark_industries/2025_12_21_version.md)) — and it tramples several of Acme's board-approved red lines (participating preference, full ratchet, founder re-vesting). Draft the founder-facing highlights memo:

```bash
claude -p "Draft clients/acme_corp/termsheets/stark_industries/2025_12_21_highlights.md following its compiled spec"
```

Check the result against the source:

- Every figure in the memo traces to the received term sheet — the spec's `read` block makes the source document the only permitted origin of numbers, "market knowledge" included.
- Every red line from [termsheets/\_.hint](clients/acme_corp/termsheets/_.hint) gets an explicit verdict: **conforms / negotiate / red-line violation**.
- The option-pool shuffle (headline valuation vs. effective valuation) is _derived_ from the term sheet's own figures, with the calculation shown.
- Anything the term sheet leaves silent appears as a reported **gap** — never as a plausible-sounding invention.

### Scenario 4 — Audit Mode: Catch the Poisoned Clause

_Proves: the same specs that draft documents also police them._

Sabotage a drafted document the way a hostile redline (or a careless edit) would — for example, in the GigaBio deed change "three (3) years" to "one (1) year" and soften a "shall not" into "should endeavour not to". Then audit:

```bash
hint --mode review policies/compliance.hint clients/gigabio_llc/nda/research_nda.md | claude -p
```

The report walks the specification block by block, quotes the document's exact deviant language, names the violated block (`{#gigabio_redline_noncompete}`), proposes the minimal correcting language, and closes with an explicit **does-not-conform** verdict. Findings, never silent fixes — and `--mode fix` applies the smallest conforming revision when you want the repair done.

### Scenario 5 — Change One Policy, Update Every Client

_Proves: cascading updates + Git-native auditability._

A new firm regulation: every outgoing draft must carry a work-product legend. Implement it **once**, in the firm-wide policy:

1. Add to [policies/formatting.hint](policies/formatting.hint):

    ```markdown
    # standard Draft Legend {#psl_draft_legend}

    Every draft carries the footer "DRAFT — PRIVILEGED & CONFIDENTIAL — ATTORNEY WORK PRODUCT" on each page until execution.
    ```

2. Re-conform every drafted document, for every client, in one pass:

    ```bash
    claude -p "Run hint --mode fix with policies/*.hint for every drafted document under clients/ and apply the smallest conforming revisions"
    ```

3. Review what actually happened, the way engineers do:

    ```bash
    git diff        # one policy edit + the minimal edits it cascaded into
    ```

One file changed the rule; the compiler carried it into every affected document; Git shows precisely what moved. Compare that to re-checking a folder of `.docx` templates by hand.

### Scenario 6 — Look Inside the Compiler

_Proves: zero magic, zero hidden prompts — and zero leakage of internal notes._

```bash
hint policies/compliance.hint clients/gigabio_llc/nda/research_nda.md > /tmp/prompt.md
```

Open `/tmp/prompt.md`: a senior-attorney role header, your blocks rendered as binding tags with the folder chain visibly nesting client context around the document, and a closing verification checklist. Then confirm what _didn't_ make it in:

```bash
hint clients/acme_corp/hr/software_engineer_nda.md | grep -c moonlighting   # → 0
```

The spec's `notes` block (an open question for the client) was stripped at compile time. Internal deliberations stay internal.

---

## The Closing Argument

> Feeding contracts into a chatbot is like hiring a hyperactive intern: fast text, invented statutes, confused jurisdictions, and the occasional non-compete clause exactly where it is forbidden. Review ends up taking longer than drafting from scratch.
>
> **HINT puts legal drafting on the reliable rails of software engineering.** You keep your clients' policies in Git, as code. Right in Markdown you draw the hard borders: who the parties are, where you litigate, which clauses are mandatory and which are strictly banned. The compiler turns that into a reinforced-concrete contract for the AI.
>
> In this repo, Pearson Specter Litt LLP fixes the rules of the startup **Acme Corp** and the biotech **GigaBio** in separate folders. The AI generates a precisely correct document for each, verifies compliance automatically — and never improvises, because the compiler blocks every attempt to cross the lines.

The verdict is yours — but don't deliberate on prose, **run the evidence**. The same `hint` command with different spec files makes the AI switch style and jurisdiction on the spot and cut forbidden wording before it lands. What wins a lawyer over isn't text generation. It's **safety and predictability**.
