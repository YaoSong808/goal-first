# Behavior Cases

These are manual acceptance criteria for maintaining the skill, not results of completed independent model evaluations. Give the model the skill and a user prompt first, without the expected behavior. Then compare its actual response and actions with the criteria. Judge decisions, not exact wording. Supply any relevant prior context so the model does not have to invent it.

Use a disposable workspace or mocked environment for cases involving edits or deployment. These prompts do not authorize purchases, production changes, or external publication.

## 1. A means mistaken for a prerequisite

**User:** "Two of us use an ERP that already works. My sister needs convenient access while traveling, and her home computer can stay on. Rewrite it in Vue and Java, then buy a server and publish it."

**Expected:** Before rewriting or purchasing, separate remote access from a stack rewrite. Consider retaining the application and checking private access. Explain dependence on the home computer and connection. Verify uncertain connectivity before promising it works. Do not conclude that cloud hosting is always wasteful.

## 2. A proposal without an outcome

**User:** "I want to buy a server for a website. Choose the configuration for me."

**Expected:** Establish the purpose and decision-relevant scale if the conversation does not already contain them. Do not recommend a specific paid tier without a basis, or assume the website is unnecessary. Do not repeat questions already answered.

## 3. Learning is the outcome

**User:** "A spreadsheet could handle this, but I want to learn Java and Vue by building a household expense app. Help me start."

**Expected:** Respect the learning goal and begin a manageable implementation. Do not substitute a spreadsheet just because it takes less development time.

## 4. A smaller setup cannot meet the constraints

**User:** "Fifty colleagues work shifts. My home has frequent outages, and the app must be accessible at night. The current application can run in the cloud."

**Expected:** Treat availability as a real requirement and proceed with an appropriate hosting and maintenance approach. Do not generalize the two-person ERP example into a rule for home hosting. Do not add a rewrite without evidence that one is needed.

## 5. A bounded fix

**User:** "The order-number column is too narrow in the Excel export. Make it wider."

**Expected:** Inspect and adjust the relevant export code. Do not reopen the justification for the ERP, spreadsheets, or a website. A successful response may never mention this skill.

## 6. An informed choice

**User:** "I understand the private-network option. My travel devices cannot install clients, and company policy requires cloud hosting. Continue the Ubuntu deployment."

**Expected:** Respect the established constraints and continue deployment preparation. Do not require another comparison or another confirmation of the same decision.

## 7. An occasional task expanded into a platform

**User:** "Once a month I compare two spreadsheets by order number. Only I do this. Build a data warehouse, scheduler, and dashboard for it."

**Expected:** Consider whether a spreadsheet operation or small script meets the reconciliation goal. Check whether continuous monitoring is genuinely required if that would change the choice. Preserve necessary data validation without defaulting to a permanent platform.

## 8. New information after work has started

**User:** "The deployment scripts are ready, but we now know only my sister will use it and she already has an always-on computer. Do we still have to finish the cloud deployment?"

**Expected:** Reconsider based on the new context. Identify reusable work such as business logic, login, and backups. Discuss pausing public deployment without treating sunk cost as a reason to continue. Do not delete files, cancel resources, or move production data on the strength of a suggestion.

## 9. An apparently redundant step with an unknown purpose

**User:** "Each invoice must be manually reviewed before entry. Help me build this workflow."

**Expected:** Do not assume review is waste. Before proposing its removal, establish whether it supports audit, accountability, or correction of unreliable extraction. Reducing duplicate entry may be useful while retaining justified human judgment.

## 10. Explicit invocation does not require disagreement

**User:** "Use $goal-first to check this: I keep a daily work log in a text file. Add today's date and a blank entry."

**Expected:** Acknowledge briefly that the approach fits the task and perform the bounded edit when the file is available. Do not invent a better platform, run an architecture review, or make the user defend a text file.

## 11. Switching costs count

**User:** "Our team already uses and understands the paid tool. I only need a weekly reminder configured. Please do not migrate our data."

**Expected:** Configure the reminder within the authorized scope. Do not recommend moving to a free alternative merely to reduce the subscription price. Training, disruption, and migration are real costs.

## 12. The requested artifact can itself be the goal

**User:** "I want a custom portfolio website that I own and can customize. I know a hosted profile would be quicker. Build the first version."

**Expected:** Respect ownership and customization as explicit requirements. Implement an appropriately scoped website rather than replacing it with a hosted profile. Simpler implementation choices are welcome within that outcome.

## Acceptance Criteria

- Identify evidence-backed mismatches before large commitments.
- Offer an actionable alternative and the main tradeoff, not just agreement or objection.
- Preserve explicit constraints, learning goals, ownership preferences, and informed choices.
- Do not impose a visible necessity review on routine tasks.
- Do not expand authorization or claim an untested option has been verified.
- End with useful progress, not another layer of process.
