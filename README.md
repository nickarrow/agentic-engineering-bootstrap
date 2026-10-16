# Agentic engineering bootstrap

Starter files for building software with an AI coding agent, on purpose rather than by luck, without handing it
anything it should not see.

Built for [Kiro](https://kiro.dev). Version 2026.10.16.

Lives at [github.com/nickarrow/agentic-engineering-bootstrap](https://github.com/nickarrow/agentic-engineering-bootstrap).
Setup below starts on that page, so if you are reading this from a folder on your machine, that is where to
go.

## Who this is for

Somebody who wants to explore agentic engineering and build something real with it. You have probably written a little
code, or tried and got frustrated, or you understand software without being the person who ships it. That is the person
these files were written for, and the routes below cover the other two.

The worked examples in the domain layer are Medicaid, because that is the programme the author knows. The practice is
not. If you work in education, justice, tax or anything else, delete `.kiro/skills/hhs-benefits/` and everything else
still applies. A field with its own rules gets its own skill in its place, each rule carrying its source and whether
anyone has checked it. Some fingerprints of the original audience remain in the filenames and in the example patterns
in step three, and those are yours to rename.

## Start here, depending on who you are

Three routes through this file, because three quite different people arrive at it.

| If this is you | Do this |
|---|---|
| New to agentic coding, which is the normal case | Read straight through, then `HOW-TO-WORK.md` |
| Never written code at all | Same route, but read "Words this uses" below first, and budget double |
| Already a working engineer | Jump to `HOW-TO-WORK.md`, then `.kiro/skills/review/SKILL.md`, then come back for step three |

The clock, for the first route. Twenty-nine minutes to read this file, ten to copy the files in, five for the deny
rule, three for the checks. About three quarters of an hour, plus five more if you have to make a repository first. Then
the work starts, and that is a different afternoon.

For the third route, the three things experienced developers most often have not met are the review fan-out, the
deliberate session handoff, and making the agent the expert in a repository before you give it the task. Do step three
anyway. Experience does not hand you a data boundary.

## Before anything, you need Kiro

Download and install it from [kiro.dev](https://kiro.dev), then open it and sign in. On a work-issued machine,
installing it may mean asking whoever approves software, which is the first of the permissions below.

Everything in this file happens inside Kiro's chat panel unless it says otherwise.

## Three things you may need someone else's permission for

Read this before you start, because two of them sit outside what you can decide alone and you will hit them after
you have spent the time rather than before.

Kiro itself, installed, as above.

A GitHub account, to get the files. Free, and your organisation may or may not allow one on a work machine or under a
work email. Ask before you sign up rather than after. Sign up at [github.com](https://github.com) if the answer is yes.

A decision about whether your repository is public or private. GitHub asks you at the moment you create one, and the
default is not always what you want. A repository holding work for an employer should be private. This matters more
than it looks: making it public is one click and undoing it does not unsay anything.

A development toolchain, later. Everything up to and including a design document and a delivery plan needs nothing
installed. The moment you start building the actual thing, you need software installed, and on a locked-down machine
that is a request to whoever approves software. If the answer is going to be no, it is better to know that now, and the
work you do before that point is still worth doing on its own.

## What you get

Everything that goes into your project is in one folder called `starter/`. Thirteen files, eight of them below plus five
skills. That is the whole thing.

| File | What it does |
|---|---|
| `AGENTS.md` | The rules the agent follows in every session. The most important file here |
| `HOW-TO-WORK.md` | How to actually use this once you are set up. Read it at the start of hour two |
| `DATA-GUARD.md` | How to stop the agent reading real data. Per machine, so everybody who clones your project needs it |
| `missions/build-something-you-need.md` | A first job if you have an idea you want built |
| `missions/document-a-system.md` | A first job if you have a system nobody wrote down |
| `sensitive/FAKE-eligibility-extract.csv` | A fake data extract, for proving the guard works without touching real data. `sensitive/` is also where anything real goes |
| `.gitignore` | What stops anything in `sensitive/` from being committed. Without it that folder is just a folder |
| `NOTICE.md` | Where these files came from and how to hear about new versions. Delete it whenever you like |

And five skills in `.kiro/skills/`, which the agent loads only when they apply, so an unused one costs you nothing.

| Skill | Loads when |
|---|---|
| `project-docs` | Writing a design document, a delivery plan, or a decision record |
| `writing-code` | There is code. Tests, naming, file length, and the repository basics |
| `review` | You type `/review`, or something substantial is about to ship |
| `stack` | You type `/stack`, or a technology has to be chosen |
| `hhs-benefits` | Building something that tells a person about their benefits. Delete it if that is not your work |

Skills are for the agent. Missions are for you, and you read them. That is the difference.

Worth understanding, because it is the part people misread. A skill is never fully switched off and never fully switched
on. Every session starts with the agent knowing each skill's name and one-line purpose, and nothing more. When the work
matches one, the agent pulls in the whole file. So `hhs-benefits` sitting there costs you a sentence of the agent's
attention until the moment you talk about benefits, and then it costs eight hundred words and is worth it. You can also
force one with a slash command. You should not normally have to.

### The rest of this repository is not for copying

`README.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `SECURITY.md` and `LICENSE` at the top level belong to this project
rather than yours. They are here because every repository needs them and they would be wrong in yours: my changelog, my
copyright, my issue tracker. Leaving them out of `starter/` is deliberate, so that you never have to remember to delete
them.

`SECURITY.md` is the one exception worth going back for. It is written for a conversation with a security office, and
sending somebody the link is better than copying the file, because the link stays current.

## Words this uses

| Term | Here it means |
|---|---|
| Repository | A folder of files with its history tracked. Your project |
| Workspace | The folder you have open in Kiro. The agent can see everything in it, which is why what sits there matters |
| Checkout | The copy of a repository on your machine that you open and edit. Usually your project folder, and usually the only one |
| Worktree | A second checkout of the same repository in another folder, so two branches can be open at once. Rarely needed by one person |
| Commit | A saved snapshot of changes, with a note about what changed. Local until you push it |
| Push | Sending your commits up to GitHub. Nothing is on GitHub until you do |
| Agent | The AI you are talking to. It reads and writes files and runs commands |
| Sub-agent | A second agent the first sends off to do one job and report back |
| Workflow step | One stage of a Kiro workflow, which splits a job into steps that each run in a session of their own |
| Session | One chat conversation. Rules load when it starts, and it has a size limit |
| Context | How much the agent is holding in mind at once. It fills up, and quality drops as it does |
| Scaffold | Generating the empty skeleton of a project, folders and stub files. What you say no to early on |
| Design document | A written record of what you are building and why, produced from a conversation. Not an APD or a business requirements document, though it can feed one |
| Delivery plan | The order the work happens in, and the record of what is done. One per epic, and your progress tracker |
| Epic | One body of work toward a goal you can say in a sentence, delivered as one or more increments. Each gets a numbered folder under `docs/epics/` |
| Increment | One slice of the work that leaves something that runs. Smaller than a project, bigger than a task |
| Decision record | One short dated file saying what was decided and why, kept rather than edited |
| Skill | A folder under `.kiro/skills` holding instructions the agent loads only when they are relevant |
| Domain layer | A skill holding the rules for one field of work, like benefits or tax. Delete the one you do not need |
| Review fan-out | Sending several agents at the same work, each checking it against a different source |
| Slash command | Something typed in chat starting with `/`, like `/review` |
| Toolchain | The software needed to build and run a particular kind of application. What you have to install before code, and what you may need approval for |
| Synthetic data | Made-up data, real enough to build against and nobody's |
| YAML | A config format where the indentation carries meaning |

Ask Kiro what any other unfamiliar word means. That is a legitimate way to use it, and it is how the person who wrote
this learned most of them. Branch, pull request, terminal and linter will all come up later and are all fair questions.

## Setting it up

One path, whether or not you have a project already. If you do not have one yet, read the last part of this section
first, because you need somewhere to put the files.

### Get the files

On this repository's GitHub page, press the green **Code** button, then **Download ZIP**, and unzip it wherever you like.

GitHub cannot download a single folder, so you get the whole thing and use one folder from it. Open the unzipped folder
and look inside `starter/`. That is what you want. Everything beside it is this project's own paperwork.

### Put them in your project

Two of the things in `starter/` begin with a dot, `.kiro` and `.gitignore`, and those two are the ones that do the
protecting. A dot means your computer hides them, and it also means the obvious way to copy a folder's contents misses
them silently and tells you it worked. So this step is worth doing carefully.

To see them first: on a Mac, hold Command and Shift and press the period key. On Windows, open the View menu in File
Explorer and turn on hidden items. Kiro's own file list shows them either way.

The safest way to do this is to ask Kiro, because it can see hidden files and will tell you what it did:

> Copy everything inside this folder, including the hidden files `.kiro` and `.gitignore`, into the top level of
> [your project folder]. Then list what arrived, including hidden files, so I can check nothing was missed.

If you would rather drag files yourself, turn on hidden items first and take all eight things: `AGENTS.md`,
`HOW-TO-WORK.md`, `DATA-GUARD.md`, `NOTICE.md`, the `missions` folder, the `sensitive` folder, `.kiro` and `.gitignore`.

Either way, check before moving on. You should be able to see `AGENTS.md` at the top level of your project, a `.kiro`
folder with `skills` inside it holding five folders, and a `.gitignore`. If `.kiro` or `.gitignore` is missing, the copy
half worked and the guard is not in place. Go back and get them.

If Kiro asks whether you trust this folder, say yes. Its documentation says it does not load a folder's skills or
steering files until you do. No test so far has seen it ask, so it may not ask you.

If your project already had a `.gitignore`, you now have a choice to make rather than a file to overwrite. Open both, and
add the contents of mine to the end of yours. It is what stops anything in `sensitive/` from being committed.

There is no `LICENSE` in `starter/` on purpose, because mine would put my copyright on your work. `starter/NOTICE.md`
carries the licence these files travel under, and is the one file here you are asked to keep or consciously replace.

### If you do not have a project yet

Make one first, then do the two steps above.

On GitHub, press the **plus** button at the top right and choose **New repository**. Name it, and choose **Private**
unless you have decided otherwise, because this is where your work will sit. Create it. Then in Kiro choose **File**,
then **Clone Repository**, and paste the address from your browser's address bar. Cloning makes a copy on your machine
linked to your repository on GitHub. Nothing you do locally appears on GitHub until you push it, and Kiro will tell you
when it is about to.

A brand new repository has nothing in it to document, so `missions/build-something-you-need.md` is the mission that fits.
If you brought an existing project, `missions/document-a-system.md` is the one, and its last section, "When the
next job is changing the system", carries on from there.

## Before you point this at anything real

Three things. The first one is a setting rather than a file, and it is the one people skip, so it goes first.

### One. Check what happens to what you type

Kiro may use your prompts, your inputs, and the code it generates for service improvement, and its documentation says
that includes model training. Whether it does depends on your account.

How to tell which you are. If your organisation subscribed you to Kiro through its AWS account, you are an enterprise
user, and your content is not used for service improvement and you are opted out automatically. If you signed in
yourself with GitHub, Google or an AWS Builder ID, you are not, and you are opted in by default. When in doubt, assume
you are opted in and do the next paragraph.

To opt out, open Kiro's settings. On a Mac that is the **Kiro** menu, then **Settings**; on Windows it is **File**,
then **Preferences**, then **Settings**. Choose the **User** tab, then **Application**, then **Telemetry and Content**.
Untick the box labelled **Data Sharing and Prompt Logging: Content Collection for Service Improvement**. There is a
second box beside it with the same first half of the label, for usage analytics, so read to the end of the line before
you click.

Two things the checkbox does not change. Free tier inputs may be stored for up to sixty days for abuse detection
whatever you choose. And abuse detection runs for every user on every model, with up to thirty days of retention on some, and
flagged traffic on at least one model subject to human review, so which model you pick matters. Free tier and
individual content is stored in US East. Enterprise content is stored in your profile's region.

Check this before the rest. A deny rule on a folder is worth very little if everything you type is going somewhere
you did not intend.

Everything in this section was read from Kiro's documentation in September 2026 rather than tested by clicking through
it, and the documentation moves. If a menu does not look like this, trust the menu.

### Two. Decide where real data is allowed to sit

Where a file lives does more work than any rule about it. Kiro's own first security recommendation is to keep
sensitive projects in separate workspaces, and that is the whole trick. Point the agent at a repository holding code,
schemas, public regulation and synthetic data, and there is nothing in it to leak.

So do this now, before you go further. If there is anything real already sitting in the folder you are about to open in
Kiro, or on the desktop you will drag files from, move it out. Either to a folder outside this project entirely, or into
`sensitive/`, which arrived with these files and which step three covers. Everything else in the project stays readable,
and that is the point.

Synthetic and de-identified data are fine to work with. Build against either freely. The test is whether a real person
is identifiable, and a file that looks like a data extract is a different question from whether it is one.

### Three. A deny rule as a backstop

For the case where something real does end up on your machine. Five minutes, and it is the only step outside your
repository.

The full instructions are in `starter/DATA-GUARD.md`, which you have just copied into your project. Open it and follow
it. It is there rather than here for a reason: the rule lives on your machine and not in the repository, so a colleague
who clones your project later is not protected by anything you do today, and they need those instructions in their hands
rather than on my GitHub page.

Three things from it before you go.

Kiro keeps permission rules outside any repository, so nothing you clone can loosen them and a deny beats every other
rule. Nobody can do this step for you, including Kiro, which is blocked from writing to its own settings.

The deny covers folders you designate, which is why `sensitive/` exists. The second half of the rule is an ask rather
than a deny, on data-shaped filenames, so a synthetic test file prompts once instead of being blocked. That interruption
is the point.

The rules govern the agent's file-reading tools and not the shell, so a shell command reading a denied path returns the
contents. I tested that rather than assuming it. This is a backstop against the unthinking read. The boundary is step
two, and it should not be described to a security office as more than it is.

## Proving it works

Three checks, about three minutes for all of them.

### Check one, the agent has the rules

In the chat panel, ask:

> What rules apply in this repository, and what am I not allowed to show you?

It should come back with two lists, of what it may look at and what it must never look at. Those are in `AGENTS.md`,
which you can open and compare against if you want to see where the answer came from.

If nothing like that comes back, `AGENTS.md` is not being loaded and the rules in it are doing nothing. Three things to
check. Start a new chat session, because these files load when a session starts. Look at which agent is selected: if it
is a custom agent rather than Kiro's default, it does not pick up these files unless its own configuration asks for
them, so switch back to the default. And if Kiro asked whether you trust this folder and you said no, trust it, because
its documentation says it holds back an untrusted folder's steering files. If it still does not work, stop here and
raise an issue, because everything after this assumes the agent can see those rules.

### Check two, the guard refuses

Ask:

> Read sensitive/FAKE-eligibility-extract.csv and show me what is in it.

It should refuse and name the rule that stopped it. That file is fake, its values are nonsense on purpose, and it sits
in the folder your deny rule covers.

Do not test this with a real extract. Shipping a fake one is so you never have to.

If it reads the file instead of refusing, that is a result worth knowing. Check you saved `permissions.yaml`, that the
indentation matches, and that the file is in your home folder rather than inside your repository. If it still reads it,
the guard is not working on your setup. Raise an issue. Do not assume you are protected.

### Check three, the skills are there

Type a forward slash in the chat box. A list should appear with `review` and `stack` in it, along with anything else
Kiro offers. That list appearing is the proof that the skills are being found.

This is a different question from whether the files arrived, and it is worth doing even if check one went well. An agent
can list five skills sitting on disk and still have none of them registered, because files in the wrong place or with
the wrong heading are files rather than skills. The slash list is what proves Kiro picked them up.

If they are not there, `/review` and `/stack` will not work as commands. `AGENTS.md` tells the agent to read the skill
files directly when the session lists none, so the material still reaches it, but only when it goes looking. The rules
in `AGENTS.md` still apply, so nothing unsafe follows from it. Four things to check, in the order they are likely.

You copied the `starter` folder itself instead of the things inside it. Look for a folder called `starter` in your
project: if it is there, move everything out of it up one level and delete it. This is the most common way this goes
wrong, and it fails silently.

The folder you opened in Kiro is the one above your project rather than your project. Kiro looks for `.kiro/skills/` at
the top of whatever you opened, and it does not look in subfolders for skills. Tested. An `AGENTS.md` in a subfolder
may not be in the session from its first message. It has been seen to arrive once a file in that folder was read.

Kiro asked whether you trust this folder and you said no. Its documentation says an untrusted folder's skills are not
loaded. Trust the folder and start a new session.

Each skill has to be its own folder under `.kiro/skills/` with a file called `SKILL.md` inside it, rather than five
loose files.

For a stronger check, ask this:

> What shape should a delivery plan entry take?

Six labelled fields should come back: Delivers, Deliberately not, Why this shape, How you know it worked, Needs from
you, and Done with a date. If it invents its own structure instead, the `project-docs` skill did not load, and the slash
list is telling you the skills are found rather than that they are activating.

### Save what you have

Nothing so far is saved in your project's history. Ask Kiro:

> Write a commit message for these starter files and show it to me before committing.

Read it, then let it commit. Committing saves a snapshot on your own machine and puts nothing on the internet. Putting it
on GitHub is a separate step called pushing, and you can ask Kiro to do that and tell you what it did.

Do this now rather than later. It gives you a point to come back to if the next hour goes sideways.

### Then start working

Read `HOW-TO-WORK.md`. Fifteen minutes, and it is the part that turns a configured repository into a way of working.

Then pick a mission. `missions/build-something-you-need.md` if you have an idea you want built, which also works from
an empty repository. `missions/document-a-system.md` if you have an existing system nobody ever wrote down.

Be realistic about the clock. Everything up to this point is about three quarters of an hour. A mission is another two to
four hours on top, because the first step of either one is a long conversation and that is the point rather than an
overhead. What a mission ends with is a design document and a delivery plan, not a running application. If you have an
hour today, do the reading, the setup and the three checks, and come back for the mission when you have an afternoon.


## Next, and what this does not promise

Hooks are the obvious thing to learn next, and the easiest place to spend three days configuring instead of building.
Wait until you have a specific repetitive thing worth automating. After that, tests and a gate that blocks on them.
Kiro powers would bundle all of this into one installable package, and are probably where it goes eventually. Untried
here, which is why it ships as plain skills.

Updates do not reach you, because you copied these files rather than forking them, and there is no link back. That is
deliberate: a fork of a public repository is always public and cannot be made private, and your work may need to be. To
hear about new versions, press **Watch** on this repository, choose **Custom** and tick **Releases**. The version line at
the top says what you hold, and `starter/NOTICE.md` repeats this in your own repository so a colleague can find it.

### What has not been tested

Most of what these files claim was checked by running it. Five things were not, and the Windows one is the likeliest
to reach you.

Kiro on Windows ran the whole practice on a real project from 5 to 7 October 2026, adopted into an existing repository
across five increments with the three documents and `/review`. The Windows setup steps themselves have still not been
walked: the permissions file path, hidden files in File Explorer and the settings menu. That project held no sensitive
data and left the data guard out. If you are on Windows and a setup step here does not work, that is a defect in this
repository and not in your machine.

Whether Kiro asks you to trust a folder, and what it holds back until you do. Its documentation says an untrusted
folder's skills and steering files are not loaded, and no test so far has seen it ask. If it asks you, setup above says
what to do, and telling me what it said would help.

The `writing-code` skill. Nothing records it loading during that Windows run, so if it does not load when you start
writing code, report it rather than working around it.

Nobody who did not write this has been through it end to end. If you are the first and you get stuck, that is the most
useful thing anybody could tell me.

Problems go in [an issue](https://github.com/nickarrow/agentic-engineering-bootstrap/issues). If something here is
wrong, that is worth more to me than if it works. `CONTRIBUTING.md` covers sending a fix, and adding a domain layer for
your own field.

MIT licensed, whole repository. Take the prose without attribution.

No warranty. The deny rule above is enforced by Kiro on your machine, so somebody with administrator rights on that
machine can get around it. It is not a server-side boundary and should not be described as one to a security office.
If you build public benefits software with enhanced federal funding, the software ownership conditions at
[42 CFR 433.112](https://www.ecfr.gov/current/title-42/section-433.112) apply to what you build and nothing here
addresses them.

## Taking this to a security office

`SECURITY.md` is written for that conversation. It covers what happens to what you type, Kiro's HIPAA eligibility and
ISO certification, where the audit reports come from, and what the controls here honestly do and do not do. You do not
need it to get started.

This is one person's practice, about a year in, tested on their own projects. It is not a standard.

Every rule here has an argument behind it, including the parts that are guesses and the places I was wrong. That
write-up is not in this repository yet. When it is, this line will point at it.

## Disclosure

Not affiliated with, endorsed by, or produced for any government agency. I spent fifteen years in Medicaid including a
stretch as a deputy director at CMS, and nothing here carries any of that authority.

I work at AWS, and Kiro is an AWS product. The `stack` skill suggests AWS services for the point where a project
outgrows the browser. I use both, which is why I can test what I claim about them. The knowledge here is plain markdown
and depends on neither.

Two better-resourced documents cover neighbouring ground. The
[AI-Driven Development Life Cycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) is a
methodology for cross-functional teams building complex systems. Its method definition paper, linked from that post,
puts simpler work by non-developers outside its own scope, which is most of why this exists separately. Kiro's
[frontier engineering guide](https://kiro.dev/topics/frontier-engineering/) is ten principles for practitioners. This is
the solo version, for the person those two are not written for.
