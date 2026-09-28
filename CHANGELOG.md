# Changelog

Notable changes to this bootstrap. Newest first. Format follows [Keep a Changelog](https://keepachangelog.com/), and
versions are dates rather than semantic versions, because nothing depends on this as a library.

The `writing-code` skill tells you to keep one of these, so this file exists partly to avoid asking for something these
files do not do themselves.

## 2026.09.24

The practice became the core, the domain became optional, and the files you copy moved into one folder. If you are on
2026.09.23, this is a restructure rather than a patch.

### Added

- Everything you copy is now in `starter/`. The top level holds this project's own paperwork and none of it travels.
  Previously the whole repository was a GitHub template, which meant every adopter received my README, my changelog, my
  contributing guidance and my copyright, and had to work out for themselves which of those were theirs to keep.
- `starter/NOTICE.md`, the one file in the payload that mentions this project. It carries the MIT notice the licence
  asks to travel, records where the files came from, and says how to hear about new versions.
- A `.gitignore` at the top level for this repository's own hygiene. A nested ignore file does not apply to a parent
  directory, so `starter/.gitignore` protects an adopting project and protects nothing here.

- `CONTRIBUTING.md`, covering how to report a problem and how to add a domain layer for a field other than benefits.
- `CHANGELOG.md`, this file.
- A `project-docs` skill naming the three documents a project keeps, the shape of a delivery plan entry, and the rule for
  when a decision has earned its own record.
- A `writing-code` skill covering tests as the thing that tells an agent when to stop, naming code after the words the
  work uses, the file length target, and the repository files an open project is expected to have.
- Four rules in `AGENTS.md` under "What the software may decide", which hold whatever the work is. They were previously
  inside the Medicaid material and would have been deleted along with it.
- A third setup check, that skills are loaded and `/review` is available.
- A step zero, install Kiro, which the previous version assumed.
- Writing rules in `AGENTS.md`, so that generated prose does not read as generated. Their absence was visible in every
  document the previous version produced.

### Changed

- Renamed from `hhs-agentic-bootstrap` to `agentic-engineering-bootstrap`. The old name told anybody outside health and
  human services that this was not for them, which is no longer true and arguably never was.
- Setup is one path instead of two. Download the ZIP, copy the contents of `starter/` into your project. The template
  button is gone, which loses a one-click start and removes the need for every adopter to clean up after it. Somebody
  starting from nothing makes an empty repository first, which is one GitHub step rather than a separate flow to
  document.
- The `LICENSE` deliberately does not travel. It says copyright 2026 Nick Aretakis, and an adopter who kept it would be
  claiming my copyright over their own work while MIT-licensing it to the world. Nobody would have noticed until
  somebody asked who owned it.
- The Medicaid material is now one deletable skill, `hhs-benefits`, rather than half of `AGENTS.md`. Deleting it is a
  supported thing to do and nothing else depends on it.
- `/review` and `/stack` moved from `.kiro/steering/` to `.kiro/skills/`. Steering inclusion modes do not work on Kiro's
  command line, so the old form was both always loaded and not available as a command there. Skills work on every
  surface, which removes a caveat rather than documenting one.
- The folder for real data is now `sensitive/` rather than `private/`. On a Mac, `/tmp`, `/var` and `/etc` are all
  shortcuts into a folder called `private`, and the deny rule matches the resolved path, so the old name also blocked
  the agent from reading system logs and temporary files. Found by hitting it.
- The audience is stated as three routes rather than one person. The previous version said you did not need to have
  written software, which was optimistic.
- The plan document is called a delivery plan everywhere, with the word mapped to sprint, to Kiro's `tasks.md`, and to
  AI-DLC's Bolt so it is not a coinage nobody recognises.
- The file length target is scoped to code. Pointed at documents it produced four files that had to agree with each
  other.
- The glossary moved above the setup instructions, because every word in it was used before it.

### Verified by running it

Four of the five setup checks were performed in a real Kiro session for the first time on 2026-09-24, in a scratch
project built by following the copy instructions.

- `AGENTS.md` loads as steering and the two lists come back, along with the four rules and the house style.
- A skill activates from a request that contains none of the words in its description. "Show a person their estimated
  monthly share of cost" loaded `hhs-benefits`, which then applied the three labels to a case the skill never mentions and
  concluded the honest product is not a calculator. Description matching works on meaning, not keywords, which is why the
  domain layer stays a skill rather than becoming always-on steering.
- The instruction to say which skills were loaded works, and goes further than asked. The agent named what it loaded,
  what it did not load, and why.
- `project-docs` returns all six delivery plan fields in order.
- The deny rule refuses the fixture and names both the rule and the file it came from, checked unprompted as part of
  answering what the rules are.
- Skills are found only at `.kiro/skills/` at the top of the opened folder. They are not discovered in a subfolder, while
  `AGENTS.md` is. This is why the kit cannot use its own skills from the top level, and why copying the `starter` folder
  instead of its contents fails silently.

Still unverified: the `writing-code` skill has had no prompt, the merge into a non-empty permissions file has not been
walked, and Windows remains documentation only.

### Fixed

- The copy instruction dropped the two files that do the protecting. "Copy the contents of `starter/`" resolves, for
  anybody using a shell, to a glob that silently skips `.kiro` and `.gitignore` and reports success. Found by a reviewer
  following the instruction literally rather than reading it. The step now warns about the dotfiles first, gives a
  prompt that asks the agent to do it and report what arrived, and tells you what to look for before moving on.
- `sensitive/*` only protected a `sensitive/` folder at the repository root, while the deny rule covers `**/sensitive/**`
  at any depth. A nested one was unreadable to the agent and perfectly committable. Now matched at any depth on all three
  designated folders.
- The payload designated `sensitive/` as the place for real data and shipped none of the instructions for guarding it,
  pointing instead at a README an adopter does not have. Since permission rules are per machine, every colleague who
  cloned an adopting project saw a folder everybody believed was guarded and was not. `starter/DATA-GUARD.md` now travels
  with the folder it is about, and the README's step three points at it rather than duplicating it.
- `NOTICE.md` carried the copyright line and not the permission and warranty text that MIT requires to travel, then told
  you the file was safe to delete. It now carries the full licence and says to keep it or copy it into your own.
- The instruction for merging into an existing permissions file was wrong in a dangerous way. Lining up the dashes is not
  sufficient, and the likeliest slip, pasting the whole block into a file that already has a `rules:` line, produces
  valid YAML that has silently discarded the rules that were there. `DATA-GUARD.md` now has the reader ask the agent to
  print the merged file, and then count the rules afterwards to catch exactly that failure.
- Seven references from inside `starter/` to the kit's own README, which would dangle in an adopter's repository. One of
  them told the reader to run a check that does not exist in their copy.
- Check three now says that a list of skills on disk is not proof that Kiro registered them, because an agent will report
  five files it found and a reader will hear that as success. The slash list is the proof. Its failure list is also
  reordered by likelihood, with copying the `starter` folder rather than its contents first.
- The review protocol gained a fifth mandate: carry the instructions out rather than read them. Three rounds of careful
  reading missed an instruction that silently dropped half the files it copied. One round of doing found it with the
  first command. The mandate list is also now explicitly not fixed, with a test for adding one, which is that it checks a
  source no other reviewer checks, and a test for dropping one, which is that its source does not exist in the work.

- Reading times now match the word counts rather than the round number I hoped for. The README is twenty-five minutes.
- Setup timings are internally consistent. The previous version said fifteen minutes and an hour at the outside in the
  same file, and the numbers added to more than either.
- `HOW-TO-WORK.md` no longer attributes records retention requirements to 42 CFR 433.112, which does not contain any.
- Accessibility standards are stated precisely: Section 508 binds to WCAG 2.0 AA, the 2024 Title II rule binds state and
  local government to 2.1 AA, and 2.2 AA is the recommendation rather than the requirement.
- The changelog guidance lists all six Keep a Changelog groups rather than four.
- `SECURITY.md` no longer says Kiro's documentation states something "plainly" that it states indirectly.
- The troubleshooting step no longer tells you to move `AGENTS.md` to the repository root. Kiro discovers it in
  subdirectories too.
- `AGENTS.md` now says what happens under a custom agent, which is that none of this loads.

### Notes on the writing rules

The house style in `AGENTS.md` grew four rules from an audit of these files, and the audit corrected three assumptions
worth recording, since they are the sort of thing a future pass will get wrong again.

"Actually" and "genuinely" look like filler and are mostly load-bearing. "Report counts you actually computed" needs the
word. Eighteen instances, nearly all kept.

Colon constructions look like drama and are labels introducing a list. "Report by severity: blocking, should fix, note."
All thirty-one kept.

Counting openers look like a tic and about half carry information. "Three checks, about three minutes for all of them"
tells you something. "Three things, in the order they matter" tells you only that a list is coming. The rule
distinguishes them rather than banning the count.

What was actually wrong: an opening line that promised two things and withheld both, a ranking preamble with an X-not-Y
buried inside it, and six phrases that rated the content instead of saying anything. Four uses of "worth knowing" stayed,
because "that is a result worth knowing" reframes a failed check as information rather than a broken setup, which is the
point of the paragraph it sits in.

One rule was corrected rather than added. "Short flat sentences" had been over-applied into staccato: no sentence in these
files runs over 24 words and the mean is under 10, while the voice reference they were written from runs 18. Uniformly
short reads as machine output the same way uniformly long does.

### Removed

- The claim that a mission ends with real work shipping. It ends with two documents, which the mission itself always
  said.
- The blunt filename rules from the travelling `.gitignore`. Ignoring every `.csv` and every `data/` folder is right for
  this repository and quietly destructive in a normal project, which would find its test fixtures silently uncommitted.
  They ship commented out, with a note saying which to enable.

## 2026.09.23

First public release, as `hhs-agentic-bootstrap`. Nine files: a README, a working agreement, a practice guide, a
security posture note, two steering files, two missions, and a deliberately fake data extract to prove the guard fires.
