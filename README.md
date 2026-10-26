# Goal First

**Understand intent at the start, assess the approach, then intervene when warranted.**

[中文介绍](README.zh-CN.md) | [Skill instructions](SKILL.md) | [Behavior cases](references/behavior-cases.md)

Goal First is a small, instruction-only skill for Codex. It asks the assistant to establish the user's intent early in a project: the problem to solve, who will use the result, what success means, and which constraints matter. With that shared understanding, it can assess the proposed approach and suggest a more direct path when appropriate.

The core sequence is **understand intent, assess fit, intervene if warranted, then advance the work**.

## Why This Exists

At the start of a project, users often express a need as a proposed solution: "build a website," "develop an app," or "automate this workflow." These requests identify an approach, but may leave the purpose, usage context, and success criteria unstated.

An assistant that immediately chooses a stack, lists features, and writes code can efficiently complete a solution that misses the user's intent. Important context may emerge only after unnecessary work has accumulated. Jumping straight to a "simpler alternative" without understanding the user can miss the goal just as badly.

This skill therefore starts with **understanding and aligning on intent early in the project**. The assistant uses existing context first. Where uncertainty could change the direction, it briefly states its working understanding and checks it with the user. Its inference is not a requirement the user has already confirmed.

Only then can it judge whether intervention is useful. If the proposed approach fits, proceed. If it introduces an avoidable detour, explain the mismatch, alternative, and tradeoff. Establish intent even when the proposal looks straightforward, rather than waiting for visible waste before asking what the user needs.

When the context already establishes intent, no extra confirmation round is needed. A bounded fix does not reopen the whole project. The aim is early alignment, not another approval process.

## What It Changes

| Situation | Expected behavior |
| --- | --- |
| A project starts with a solution name but an unclear purpose | Understand intent and resolve direction-changing uncertainty before selecting an approach. |
| The user corrects the assistant's interpretation | Update the understanding and recommendation instead of defending an inferred "real need." |
| A rewrite is assumed necessary for deployment | Separate the two decisions before starting the rewrite. |
| A large platform is proposed for an occasional task | Consider an existing tool or a small script, with the relevant tradeoff. |
| Important context changes midway through a project | Revisit the plan and preserve useful work. |
| The task is a small, well-defined fix | Do the fix. No visible goal-review ceremony. |
| Learning, ownership, or team standards explain the choice | Respect those goals and constraints. |
| The user already understands the tradeoff and has decided | Continue; do not keep arguing. |

The skill compares **total burden**: setup, everyday use, maintenance, money, reliability, data consistency, and switching costs. Fewer components or a cheaper subscription do not automatically mean a better solution.

## A Useful Intervention

Suppose the user says, "Build a website so I can handle business away from home." First establish the purpose and available resources, before choosing technologies or discouraging a website:

> I understand that you want to handle business while away. Is this primarily for you, or also for employees or customers? Do you already have an application that handles that work?

If the user then explains that only one or two people use an existing ERP and a home computer can stay on, there is a basis for a recommendation:

> Since the goal is remote access to the existing ERP, rewriting its frontend and backend is not a prerequisite. We can check whether private access meets the need. That depends on the computer and home connection staying available; cloud hosting is worth considering if they cannot.

Travel is one illustration. The same reasoning applies to new products, analysis, learning projects, purchases, and process design. Verify decision-critical conditions rather than presenting a plausible option as already tested.

## What It Does Not Do

- Treat "simpler" as permission to remove required capabilities or change the requested deliverable.
- Declare "what you really need" and redirect the project before understanding the user's intent.
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
Use $goal-first. I want a customer management tool, but the requirements
are still unclear. Use the available context to understand my goal,
clarify what could change the direction, and then assess suitable approaches.
Do not start by choosing a technology stack.
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

The [14 behavior cases](references/behavior-cases.md) cover early intent clarification, user corrections, useful interventions, and cases where the assistant should simply proceed. They are acceptance criteria, not a claim of a measured success rate or completed independent model evaluation.

To assess a change, give a model the skill and a realistic prompt without showing it the expected answer. Compare its actual decisions and actions with the criteria. Include routine fixes and informed choices: avoiding unnecessary interruptions matters as much as catching overcomplicated plans.

If the Codex skill-creator validator is available, run its `quick_validate.py` against this folder. That checks structure and frontmatter, not the quality of the model's judgment. Also check local links and metadata after edits.

Contributions should start with a concrete failure or useful behavior case. Prefer a narrow correction over another universal rule. Keep instructions concise and examples in the reference file. A new framework, service, or automated test pipeline needs a demonstrated benefit before it belongs here.

This skill provides guidance, not runtime enforcement. Results depend on the model, the host, and the context available to it. A correct outcome can be "your existing plan is appropriate; let's proceed."

## License

[MIT](LICENSE). Use, modify, and redistribute it, including commercially, while retaining the required copyright and license notice.
