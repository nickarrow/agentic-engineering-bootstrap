# Contributing

Report something broken, or add a domain layer for your own field. The first is more useful to me than the second.

## Tell me something is wrong

The most valuable contribution is a report that something here does not work. Open
[an issue](https://github.com/nickarrow/agentic-engineering-bootstrap/issues) and say what you did, what you expected,
and what happened. A step that failed on Windows, a menu that has moved, a command that no longer exists, a claim that
is out of date. All of that is worth more to me than a compliment.

Two gaps I already know about and would particularly like reports on. The Windows setup steps, the
permissions file path, the hidden-file toggle and the settings menu, were written from documentation and have not been
walked on a Windows machine, though the copy-and-build half of the practice has run on Windows. And nobody who did not
write this has been through it end to end, so the first person who does and gets stuck is telling me the most important
thing anyone has.

## Add a domain layer for your own field

The practice in `starter/` is domain-neutral. `starter/.kiro/skills/hhs-benefits/` is one layer on top of it, and it
exists because health and human services is the field the author knows.

The same shape works for education, justice, tax, child welfare, nutrition assistance, housing, or anywhere else that
software tells a person something they can be denied by. If you know one of those fields, that layer is worth more
coming from you than from me.

To add one, make a new folder under `starter/.kiro/skills/` with a `SKILL.md` in it. If `hhs-benefits` is still present,
copying it is the fastest start. Either way the frame is the same and only the specifics change:

- What the software may not decide on its own, and why
- What it has to be able to explain, to whom, and on what timescale
- How a number or a status shown to a person has to be labelled
- What obligations attach to accessibility, language, and a non-digital route
- Which citation every encoded rule has to carry
- Which authority a reader should cite instead of citing your file

There is a second shape, for a field where nobody can be denied anything and the risk is a wrong answer rather than an
unjust one: a sport's scoring, a pricing model, a simulation, a calculator. The frame there is lighter. Give each
encoded rule its source: the governing body's article and clause, or the data provider's field. List the quirks of the
data source you depend on. Mark every item as verified, with the method and the date, or as unverified and taken on
trust. The point is the same as the benefits frame: an agent should be able to tell a checked rule from a guess without
leaving the file.

Two rules on the frontmatter. The `name` must match the folder name exactly, and the `description` is what decides
whether the skill loads at all, so it needs the words somebody would actually use when describing that work. A
description that only says what the skill contains will never activate.

Keep it to one file and keep it deletable. A domain layer may sharpen the four rules in `starter/AGENTS.md` and may not
loosen them, and nothing outside `starter/.kiro/skills/` may depend on any domain layer existing. If you find a file in
`starter/` that leans on one, that is a bug worth reporting on its own.

## Where things live

One practical note before anything else. Kiro looks for `.kiro/skills/` at the top of whatever folder you opened, and it
does not find skills in a subfolder. So working on this repository from the top level gets you none of the five
skills, and `starter/AGENTS.md` may not be in the session from its first message. It has been seen to arrive once a file
in `starter/` was read. `/review` will not be available while you edit the files that describe it.

If you are working on the payload, open `starter/` as the workspace. If you are working on this repository's own
paperwork, the top level is fine and you are doing it without the tooling. That is a real cost of the two-level layout
and it was not obvious until somebody tested it.

Two levels, and the split is the point.

The top level is this project's own paperwork: this file, `README.md`, `CHANGELOG.md`, `SECURITY.md`, `LICENSE` and the
top-level `.gitignore`. None of it travels.

`starter/` is the payload. It is what somebody copies into their own project, so it must contain nothing about this
project: no changelog, no copyright of mine, no issue tracker, no setup instructions.

Two files in there name this repository and both have to. `starter/NOTICE.md` carries the MIT notice and lets an adopter
trace the files back here. The `stack` skill links the AWS disclosure, because a file that recommends AWS services has to
say who wrote it. If you find a third, it is probably pollution.

If you are adding something, work out which level it belongs to first. The test is whether it would still make sense
sitting in a stranger's repository with their name on it.

## House rules

One change per pull request. A domain layer and a fix to the README are two pull requests, even if they are two
minutes apart.

Commit subjects use a [Conventional Commits](https://www.conventionalcommits.org/) prefix: `feat:`, `fix:`, `docs:`,
`refactor:`. The commit body is where the reasoning goes, and a long body is welcome. Several commits in this history
are longer than the change they describe, on purpose.

Follow the writing rules in `starter/AGENTS.md`. No em-dashes, varied sentence length, admissions without a clause that
rescues them. If your addition reads as though a model wrote it, it will get sent back, and that applies to mine too.

Say what you verified and what you did not. A claim in this repository is expected to name its source or admit it has
none. "I read this in the documentation" and "I ran this and watched it happen" are different claims and get written
differently.

Do not add a file without saying what it displaces. The reading budget is the binding constraint here and it is already
over. New material that loads on demand, meaning a skill, is much easier to accept than new material everybody has to
read.

## Maintenance, honestly

One person maintains this, in gaps between other work. Issues will get read. Pull requests may sit. If it stops being
tended, the README will say so with a date rather than going quiet.

If you need something with a support commitment behind it, this is not that, and AWS publishes guidance in this space
that comes with people attached. Your account team is the route to it.

MIT licensed. By contributing you agree your contribution ships under the same licence.
