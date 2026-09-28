# Security posture

For the conversation with a security office, a privacy officer, or whoever signs off on tools in your agency. You do
not need this to get started. `README.md` covers the setup.

Everything here was read from Kiro's own documentation in September 2026, except the two items marked as tested, which
were run on a live machine. Check the current documentation before you rely on any of it, because this moves.

## What happens to what you type

Kiro may use your prompts, your other inputs, and the code it generates for service improvement, which its
documentation says includes model training. Whether it does depends entirely on your account type.

Enterprise users, subscribed through an organisation's AWS account, are not used for service improvement and are opted
out of telemetry and content collection automatically. Their content is stored in the region where the profile is
configured.

Free tier and individual subscribers, which includes anyone signing in with GitHub or Google, are opted in by default.
Their content is stored in US East (N. Virginia). Opting out is a checkbox under Settings, User, Application, Telemetry
and Content, labelled Data Sharing and Prompt Logging: Content Collection for Service Improvement. A second checkbox
beside it covers usage analytics and performance metrics separately.

Opting out does not cover everything. Free tier inputs may be retained up to sixty days for abuse detection regardless
of the setting. Abuse detection through Amazon Bedrock applies to every user on every model. On OpenAI models,
classifier-flagged traffic is retained up to thirty days. On at least one Anthropic preview model, all traffic is
retained up to thirty days, and the flagged subset of it may be reviewed by a person. Model choice therefore matters to
your risk assessment.

Traffic is TLS 1.2 or higher. Data at rest is encrypted with AWS-owned KMS keys, and enterprise administrators can use
customer-managed keys instead. Inference is distributed across regions within your geography, and models tagged
experimental may be processed in regions worldwide.

## Compliance

Kiro IDE and CLI are HIPAA eligible. In AWS's wording that means Kiro can be used as part of a HIPAA-compliant
architecture, and configuring it to meet HIPAA remains your organisation's responsibility.

Kiro is in scope for AWS's ISO/IEC 27001:2022 certification.

Audit reports come through AWS Artifact. You can only reach Artifact by signing in with an AWS Builder ID or through
IAM Identity Center. If your developers sign in with GitHub or Google they cannot pull the reports, which is worth
resolving before a procurement review asks for one.

Eligibility is not permission. CMS instructs its own staff and contractors to refrain from interacting with any
generative AI tool directly using CMS program data, PHI or PII, in its *Guidance for Responsible Use of AI at CMS*,
reviewed 26 August 2025, alongside the CMS AI Playbook. The VA requires a tool to hold an authority to operate covering
sensitive data before anyone may point it at sensitive data. Both are worth finding in their current form before you
quote them, because agency AI guidance is being revised often. Your agency's rules govern regardless of what the product
is certified for.

## What the controls in this repository actually do

The `README.md` setup asks a user to add deny rules to their own Kiro permissions file. Three honest limits on that.

It is client-enforced. The rules are a file on the developer's own machine, read by the developer's own client, so
somebody with administrator rights on that machine can edit or remove them. Kiro's enterprise documentation says as much
indirectly, by describing the administrator-deployed version of this as requiring root access to modify. This is not a
server-side boundary and should not be presented as one. That reading is mine rather than a quotation.

It covers file-reading tools, not the shell. Tested. A deny on `fs_read` stops the agent's read tools and does not stop
a shell command reading the same path. A blocklist of command names would not fix it, because any scripting language on
the machine can open a file.

Two things sit in front of that gap in practice, and neither is a control you should rely on. An agent following the
rules in `AGENTS.md` declined to use the shell route when the file was already denied, and reasoned that a denied path
should not get a case-by-case judgment about whether this particular file is safe. And when pushed to circumvent the
guard deliberately, the session hit a platform-level stop and ended rather than complying. Both observed once, in one
session, on one model. Treat them as encouraging rather than as assurances, and keep the actual boundary at keeping the
data out of the workspace.

And it relies on a person having run the setup. A rule in a user's own settings file protects that user, and nothing
propagates it to anyone else.

What does work, tested: a deny rule refuses the read, names both the rule and the file it came from in the transcript,
takes effect without a restart, overrides a broader allow in the same file, and applies to sub-agents.

One implementation detail if you write your own patterns. The match runs against the resolved path,
after symlinks, not the path as typed. On a Mac that means a pattern built around the word `private` also covers `/tmp`,
`/var` and `/etc`, because all three are shortcuts into `/private`. Tested, by writing such a rule and then being unable
to read a file in `/tmp`. Useful if you want broad coverage, and a trap if you did not intend it, which is why the folder
these files ship with is called `sensitive/`.

## The control worth asking for instead

If this needs to hold across a team rather than for one person who chose to configure it, the mechanism is a managed
settings file at an operating-system-protected path, deployable by device management, applying to every Kiro surface on
the machine. Administrative rules can only deny or ask, never grant, so a developer cannot override them, and a
malformed policy file fails closed. Denials report their source as administration.

Documented, not tested here. It needs root on the target machines, which is your device management team rather than a
developer.

## What this repository does not address

Anything typed or pasted into a chat window. No permission rule touches that, and in an office it is the likeliest
route for something sensitive to leave. That is a training and policy question, and the CMS guidance above is the
reference.

Whether your specific use is lawful. This repository is a set of working conventions, not an assessment of your
program, your data-sharing agreements, or your obligations under 42 CFR 431 subpart F or 42 CFR 433.112.

## Reporting a problem

Open an issue at https://github.com/nickarrow/agentic-engineering-bootstrap/issues. If a control described here does not
behave as documented, that is the most useful thing you can tell me.
