---
name: hhs-benefits
description: Use when building anything that tells a person something about their benefits, eligibility, or a determination about them. Covers Medicaid and other health and human services programs. Rules for what software may and may not decide, how a number shown to a person must be labelled, notice and appeal obligations, accessibility as legal exposure, and carrying policy citations in code. Delete this file if the work is not about benefits.
---

# Building software about somebody's benefits

This is the domain layer. The worked examples are Medicaid, because that is the programme the author knows. The rules
are not specific to it: the case law behind them runs through unemployment insurance and veterans' benefits as well,
and the parts about what software may tell a person apply to any benefit anyone can be denied.

If the work has nothing to do with benefits, delete this file. Nothing else in the repository depends on it.

If the work is in another public-service domain, this file is the shape to copy. Child welfare, nutrition assistance,
education, tax and justice all have the same structure: a rule about what the software may decide, a rule about what it
must be able to explain, and a citation obligation. The specifics change and the frame does not.

## Why the four rules in AGENTS.md are what they are

`AGENTS.md` already bars a model from the path of a decision about a person, requires a replayable and explainable
determination, requires a printable record, and requires a citation on every encoded rule. This is the evidence behind
those four, and the sharper version for benefits work.

Every published failure in this field has the same shape. A machine reached a legal conclusion from proxy data, nobody
reviewed it, and the notice could not explain itself. Courts have ruled on the notice and the process more often than
on the arithmetic.

## The notice matters as much as the number

A correct figure in a notice somebody cannot read or act on is still the failure. Copy, the route to the agency,
appeal rights, language coverage and accessible presentation are part of the product, not packaging around it.

The printable record that `AGENTS.md` asks for has a specific name here. It is what somebody brings to a fair hearing,
and a person with no server-side copy of their own arrives with nothing.

Accessibility carries more weight in this field than in most, because several benefit exclusion categories are
disability-based, which turns an inaccessible interface into a discrimination question rather than a quality one.
Consensus guidance for Medicaid eligibility work recommends WCAG 2.2 AA, which is stricter than either standard that
binds, and the non-digital route is a requirement rather than a courtesy.

## Label every number shown to a person

Numbers shown to a person get one of three labels:

- **Computed** follows from their own input by a published formula. Show the number, the formula and the citation.
- **Conditional** follows given a policy choice you do not know. Show it and name the choice.
- **Deferred** depends on facts only the agency has. Do not compute it. Ask the screening question and say who to
  ask.

A hedge with no next action is worse than a verdict. If you cannot name the next action, the copy is not finished.

## Encoded policy carries its lineage

Every rule in code carries the manual section, the URL, the statute or regulation, and a plain paraphrase of what it
means. Anything that cannot carry a citation is a guess, and guesses get labelled rather than shipped quietly.

Nothing that policy can change gets hardcoded. State variation turns a hardcoded threshold into a fork per state.

Use the words the programme uses. The vocabulary rule in the `writing-code` skill matters more here than almost
anywhere, because when the manual says redetermination and the code says refresh, that gap is where a policy defect
hides until somebody loses coverage.

## What to cite when somebody asks

Cite the agency's own authority rather than this file. For Medicaid work that means CMS, whose *Guidance for
Responsible Use of AI at CMS* tells its own staff and contractors to refrain from interacting with any generative AI
tool directly using CMS program data, protected health information or personally identifiable information. Find the
current version before quoting it. An agency believes its own guidance before it believes a repository.

The de-identification standard at [45 CFR 164.514](https://www.ecfr.gov/current/title-45/section-164.514) is the line
that matters for data: data de-identified to that standard is no longer protected health information and sits outside
the Privacy Rule, and synthetic data never was inside it. The test is whether a real person is identifiable. A file
that looks like a data extract is a different question from whether it is one.

If the work is built with enhanced federal funding, the software ownership and licensing conditions at
[42 CFR 433.112](https://www.ecfr.gov/current/title-42/section-433.112) attach to what you build. Nothing in this
repository addresses them.
