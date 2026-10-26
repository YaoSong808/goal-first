# Goal First

**Reach the goal without unnecessary work.**

[中文介绍](README.zh-CN.md) | [Skill instructions](SKILL.md) | [Behavior cases](references/behavior-cases.md)

Goal First is a small, instruction-only skill for Codex. It helps an assistant notice when a requested implementation adds avoidable work, suggest a simpler sufficient approach, and then get on with the task.

The point is not to challenge every request. It is to distinguish **what the user needs** from **the method they currently know** before a costly commitment.

## Why This Exists

A working application used by one or two people needs to be accessible while traveling. A seemingly natural plan follows: rewrite the frontend and backend, buy a server, publish a website, then maintain the deployment.

But the actual need may be convenient access to the existing application. If an existing computer and a private connection meet the reliability requirements, a rewrite and public deployment may add little value. If they cannot meet those requirements, cloud hosting may be exactly the right choice.

The missed opportunity is not "using the cloud." It is failing to check whether each step helps achieve the actual goal.

Goal First makes that check part of the assistant's judgment without turning it into another mandatory process.

## What It Changes

| Situation | Expected behavior |
| --- | --- |
| A rewrite is assumed necessary for deployment | Separate the two decisions before starting the rewrite. |
| A large platform is proposed for an occasional task | Consider an existing tool or a small script, with the relevant tradeoff. |
| Important context changes midway through a project | Revisit the plan and preserve useful work. |
| The task is a small, well-defined fix | Do the fix. No visible goal-review ceremony. |
| Learning, ownership, or team standards explain the choice | Respect those goals and constraints. |
| The user already understands the tradeoff and has decided | Continue; do not keep arguing. |

The skill compares **total burden**: setup, everyday use, maintenance, money, reliability, data consistency, and switching costs. Fewer components or a cheaper subscription do not automatically mean a better solution.

## A Useful Intervention

An intervention should identify a specific mismatch, offer a workable alternative, explain the main tradeoff, and lead to progress. Usually a few sentences are enough:

> You need convenient access to the existing ERP while traveling. Rewriting its frontend and backend is not a prerequisite for that. Since only two people use it and an existing computer can stay on, we can first check whether private access meets the need. That depends on the computer and home connection staying available; cloud hosting becomes more attractive if those are unreliable.

This is an illustration, not a script to repeat on every task. The assistant should verify facts that would change the decision, not claim an untested option already works.

## What It Does Not Do

- Treat "simpler" as permission to remove required capabilities or change the requested deliverable.
- Turn every request into an interview, comparison table, scorecard, or approval gate.
- Assume the user is wrong because they are unfamiliar with implementation details.
- Reject cloud hosting, custom software, or ambitious projects as a category.
- Override an informed decision or repeatedly reopen settled choices.
- Delete existing work, cancel services, move data, or spend money merely because an alternative was suggested.

The same principle applies to the skill itself: its decision check should cost less than the avoidable work it is likely to save.

## Install

This repository is the skill folder: `SKILL.md` is at its root. It needs no application server, package installation, API key, or separate service. You do need a compatible agent environment that supports skills.

### With Codex's Skill Installer

In an environment with `$skill-installer`, ask:

```text
Use $skill-installer to install https://github.com/YaoSong808/goal-first.
The skill is at the repository root; install it with the name goal-first.
```

The installer should use the skills location configured for your environment. If a copy already exists, update that copy deliberately instead of installing a duplicate.

If the installer download fails, use the full manual clone below. Some installer versions omit subdirectories when their Git fallback selects a repository-root skill. A complete installation includes `agents/openai.yaml` and `references/behavior-cases.md`, not just `SKILL.md`.

### Manually

For a fresh installation on macOS or Linux, using the user-level location in the [official skills documentation](https://learn.chatgpt.com/docs/build-skills):

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/YaoSong808/goal-first.git ~/.agents/skills/goal-first
```

Some installations manage skills in `$CODEX_HOME/skills` or `~/.codex/skills`. Use the location your environment recognizes; do not install the same skill in both locations. If the skill is not listed, start a new session or restart the client.

For a manually cloned copy, update from its directory with `git pull --ff-only` after checking for local edits. If you installed through an installer, use that environment's supported update workflow.

## Use

Explicitly invoke the skill with a request such as:

```text
Use $goal-first to check this plan before we build it.
I need to compare two spreadsheets once a month, but I was planning
to build a warehouse, scheduler, and dashboard. What is sufficient?
```

Or:

```text
Use $goal-first. We chose cloud hosting because our home connection
is unreliable and staff need access at night. Check for unnecessary
steps within that decision, then continue the deployment work.
```

Automatic selection is enabled through `allow_implicit_invocation: true`. This permits the host to select the skill when the request matches its description; it does not guarantee invocation on every request. Explicit invocation is useful when you want a deliberate check. See the [official skills documentation](https://learn.chatgpt.com/docs/build-skills) for your client's invocation interface.

The core instructions are in English for maintainability. The skill asks the assistant to use the user's language; it includes a Chinese starter prompt and bilingual display name.

## Repository Layout

```text
goal-first/
|-- SKILL.md                     Instructions loaded when the skill applies
|-- agents/openai.yaml           Display metadata and invocation policy
|-- references/behavior-cases.md  Maintenance acceptance scenarios
|-- README.md                    English introduction and usage
|-- README.zh-CN.md              Chinese introduction and usage
|-- LICENSE                      MIT license
`-- .gitignore                   Local artifacts excluded from version control
```

The README files and behavior cases are not required reading during ordinary tasks. There are no execution scripts, background jobs, or dependencies bundled with this skill.

## Validation and Contributions

The [12 behavior cases](references/behavior-cases.md) cover both useful interventions and cases where the assistant should simply proceed. They are acceptance criteria, not a claim of a measured success rate or completed independent model evaluation.

To assess a change, give a model the skill and a realistic prompt without showing it the expected answer. Compare its actual decisions and actions with the criteria. Include routine fixes and informed choices: avoiding unnecessary interruptions matters as much as catching overcomplicated plans.

If the Codex skill-creator validator is available, run its `quick_validate.py` against this folder. That checks structure and frontmatter, not the quality of the model's judgment. Also check local links and metadata after edits.

Contributions should start with a concrete failure or useful behavior case. Prefer a narrow correction over another universal rule. Keep instructions concise and examples in the reference file. A new framework, service, or automated test pipeline needs a demonstrated benefit before it belongs here.

This skill provides guidance, not runtime enforcement. Results depend on the model, the host, and the context available to it. A correct outcome can be "your existing plan is appropriate; let's proceed."

## License

[MIT](LICENSE). Use, modify, and redistribute it, including commercially, while retaining the required copyright and license notice.
