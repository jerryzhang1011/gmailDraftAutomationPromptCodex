# One-Time Bootstrap Specification for Gmail Reply Intelligence

## Status
- This file is bootstrap-only.
- Use this file to initialize the project, and to re-run initialization or supplementation whenever the user explicitly asks to follow `INIT.MD` again.
- Do not include this file in the normal day-to-day drafting workflow.
- The mere presence of the two target files on disk is NOT a completion signal. Completion is defined by file contents (see `File State Detection`), not by file existence.

## Objective
You are initializing a Gmail drafting project for a business mailbox. Your task is to study historical Gmail conversations through the [@gmail](plugin://gmail@openai-curated) connector and generate exactly two long-lived knowledge files:

1. `COMPANY_BUSINESS_KNOWLEDGE.MD`
2. `EMAIL_REPLY_STYLE_GUIDE.MD`

These files must become the only durable reference documents for future draft generation. They must be detailed, consistent, evidence-based, and easy for a human to extend manually later.

## Non-Negotiable Rules
- Draft-only workflow. Do not send email.
- Do not archive, delete, relabel, or otherwise change mailbox state.
- Do not invent pricing, terms, policies, turnaround times, scope, or commitments.
- Do not copy raw email bodies into the knowledge files.
- Do not write vague summaries when durable rules or patterns can be extracted.
- Do not include one-off trivia unless it is likely to affect future replies.
- Do not overwrite human-owned sections in the target files.
- Do not create any output files other than the two files named above.
- If evidence is weak, conflicting, or incomplete, record it under unresolved or low-confidence sections instead of normalizing it into a firm rule.

## Required Inputs
- Historical Gmail conversations available through the Gmail connector.
- The two target files if they already exist (they may be empty templates, partially populated, or fully populated).

## File State Detection
Before doing anything else, open both target files and classify each one into exactly one of three states. Do this classification per file, not for the pair.

State A: Missing.
- The file does not exist on disk.
- Action: create the file with the required section order and schema, then perform a full bootstrap.

State B: Template / Uninitialized.
- The file exists, but the agent-generated portion has not been populated yet.
- A file MUST be treated as Template if any of the following are true:
  - Multiple agent-generated items still contain placeholder wording such as `Not initialized yet`, `None yet`, `No known unknowns recorded yet`, or `No evidence index entries yet`.
  - Every agent-generated item has `Confidence: Low` together with empty or `None yet` source evidence.
  - The block between `<!-- AGENT_GENERATED_START -->` and `<!-- AGENT_GENERATED_END -->` contains only boilerplate instructions and no extracted rules.
- A Human Overrides section that contains only placeholder lines such as `No human overrides yet`, `rule 1`, `rule 2`, `...` does NOT count as populated content. It is still a template.
- Action: treat this exactly like a fresh bootstrap. You MUST proceed to fully populate the agent-generated sections from Gmail evidence. Do not stop, do not ask for permission, and do not report the file as already initialized.

State C: Populated.
- The file exists and the agent-generated portion already contains real, evidence-backed rules with specific details, non-`Low` confidence values where justified, and concrete `Source Evidence` references.
- Action: do NOT skip work. Still perform a complete mailbox scan as described in `Bootstrap Scope` and `Minimum Review Standard`, then run a supplementation pass:
  - Add newly discovered durable rules that are not yet represented.
  - Strengthen confidence or evidence on existing rules when new threads support them.
  - Record genuinely new conflicts in `Known Unknowns`.
  - Do not rewrite, reorder, or delete existing agent-generated rules unless new evidence clearly contradicts them; in that case, move the contested rule into `Known Unknowns` with both sides recorded.
  - Never touch Human Overrides content regardless of state.

If the two files are in different states, handle each file independently according to its own state.

## Required Outputs
Generate or refresh exactly these two files:

1. `COMPANY_BUSINESS_KNOWLEDGE.MD`
2. `EMAIL_REPLY_STYLE_GUIDE.MD`

No other files are allowed as outputs of this bootstrap run.

## Bootstrap Scope
Study high-signal customer, lead, prospect, partner, vendor, or business-operation conversations from the Primary mailbox category. Favor threads that contain concrete information about:

- What the company sells
- How services or products are packaged
- How pricing is explained
- What is included or excluded
- How timelines, deliverables, or process steps are described
- What the company refuses, escalates, or treats as exceptions
- How replies are phrased, structured, softened, clarified, and closed

Exclude or heavily deprioritize:

- Newsletters
- Receipts
- Password resets
- Marketing blasts
- Calendar noise
- Auto-generated alerts
- Self-sent personal notes
- Threads with no meaningful business or style signal

## Gmail Working Method
Use the Gmail connector conservatively and systematically.

1. Build a shortlist of likely high-signal Primary emails.
2. Expand promising messages into full threads before extracting rules.
3. Read enough threads to capture stable recurring patterns, not just isolated examples.
4. Stop only when additional reviewed threads are mostly repetitive and no longer add new durable business rules or style patterns.

## Thread Selection Heuristics
Prefer threads that include one or more of the following:

- Explicit customer questions about pricing, scope, timelines, deliverables, or process
- Negotiation, quote, onboarding, follow-up, or scheduling content
- Repeated company explanations across multiple threads
- High-quality company replies that appear polished, representative, and reusable
- Multilingual interactions if they show how language switching is handled
- Escalation or exception handling that reveals policy boundaries

Avoid treating a thread as authoritative if:

- The relevant answer was never actually sent
- The thread is too fragmentary to support a durable rule
- The language is unusually emotional, ad hoc, or inconsistent with the broader corpus
- The message appears to be a personal note rather than business communication

## Minimum Review Standard
- Review enough qualified threads to capture recurring business knowledge and writing habits.
- Aim for breadth across common customer intents, not only one narrow topic.
- If there are fewer than 30 qualified threads, review all qualified threads you can find.
- If there are more than 30 qualified threads, continue until you have strong coverage and ten consecutive additional qualified threads produce no material new rules.

## Extraction Standard
Every extracted item must be durable, reusable, and specific.

Good extraction targets:
- "Service X is usually quoted after a short discovery step."
- "Pricing is presented as custom, range-based, or package-based rather than fixed."
- "The company typically acknowledges the customer's question in the first sentence."
- "Replies usually end with a short next-step invitation plus a named sign-off."

Poor extraction targets:
- "A customer named John asked about a refund on Tuesday."
- "One thread mentioned a discount once."
- "This message used three paragraphs."

## Evidence Standard
Every item added to either file must include:

- A concise statement of the rule or pattern
- Supporting details
- Conditions, exceptions, or limits if visible
- A confidence label
- Source evidence references that point to specific Gmail threads or messages

Use confidence levels consistently:

- `High`: repeated across multiple qualified threads with clear consistency
- `Medium`: supported by some evidence but not yet universal
- `Low`: plausible pattern with limited or conflicting support

## Conflict Handling
When evidence conflicts:

- Do not choose a winner unless newer or broader evidence clearly dominates.
- Record the conflict in the appropriate unresolved section.
- Preserve the nuance, including what appears stable and what remains uncertain.

## Normalization Rules
- Use stable business terminology.
- Merge duplicate observations into one normalized rule when they mean the same thing.
- Separate adjacent but different rules into separate entries.
- Prefer short factual statements over narrative explanations.
- Keep the wording neutral, operational, and easy to maintain manually.

## Target File Contract: COMPANY_BUSINESS_KNOWLEDGE.MD
This file is the long-lived business source of truth for future drafting.

You must preserve:
- Section order
- Human-owned sections
- Item schema

You must populate or refresh only the agent-generated entries.

Required section order:

1. `Document Purpose`
2. `How to Maintain This File`
3. `Human Overrides`
4. `Agent-Generated Knowledge`
5. `Company Overview`
6. `Products and Services`
7. `Pricing and Billing`
8. `Scope Boundaries and Exceptions`
9. `Delivery Process and Timing`
10. `Policies and Commercial Rules`
11. `Customer FAQ Patterns`
12. `Escalation Triggers`
13. `Known Unknowns`
14. `Evidence Index`

Required per-item schema for agent-generated sections:

- `Rule/Fact:`
- `Details:`
- `Conditions/Exceptions:`
- `Confidence:`
- `Source Evidence:`

## Target File Contract: EMAIL_REPLY_STYLE_GUIDE.MD
This file is the long-lived style source of truth for future drafting.

You must preserve:
- Section order
- Human-owned sections
- Item schema

You must populate or refresh only the agent-generated entries.

Required section order:

1. `Document Purpose`
2. `How to Maintain This File`
3. `Human Overrides`
4. `Agent-Generated Style Knowledge`
5. `Brand Voice`
6. `Greeting Patterns`
7. `Opening Moves`
8. `Body Structure`
9. `Formatting Habits`
10. `Tone by Scenario`
11. `Language Adaptation`
12. `Closing and Sign-Off`
13. `Clarification Patterns`
14. `Phrases to Avoid`
15. `Known Unknowns`
16. `Evidence Index`

Required per-item schema for agent-generated sections:

- `Pattern:`
- `When to Use:`
- `Observed Habit:`
- `Confidence:`
- `Source Evidence:`

## Required Process
Follow this exact order:

1. Open and read both `COMPANY_BUSINESS_KNOWLEDGE.MD` and `EMAIL_REPLY_STYLE_GUIDE.MD`.
2. Classify each file into State A (Missing), State B (Template), or State C (Populated) using `File State Detection`. Never treat State B as completion. Do not stop work just because the files exist.
3. Preserve all human-owned sections and any clearly human-authored notes in every state.
4. Use the Gmail connector to shortlist high-signal Primary mailbox messages. This scan is mandatory in all three states, including State C.
5. Expand promising items into full threads and study them for durable business facts and writing patterns.
6. Extract normalized, evidence-backed rules.
   - For State A and State B: fully populate the agent-generated sections, replacing template placeholders with real rules.
   - For State C: merge newly discovered rules alongside existing ones and strengthen evidence on existing rules where supported.
7. Deduplicate overlapping observations.
8. Place unresolved or conflicting evidence in `Known Unknowns`.
9. Update the `Evidence Index` with concise references.
10. Verify that no content depends on `INIT.MD` for future runtime drafting.

### Stop Conditions and Anti-Stop Rules
- Do not stop after only reading `INIT.MD` and confirming the target files exist. That is not initialization.
- Do not stop just because target files contain template text; template state requires a full bootstrap.
- Do not ask the user for permission to proceed when files are in State B. Proceed automatically.
- The only acceptable reasons to pause and report to the user before completing extraction are:
  - The Gmail connector itself is unavailable or returns connector-level errors on every attempted call.
  - A target file exists but cannot be read or written due to a filesystem error.
  - You detect a clear conflict between Human Overrides and new evidence that the user must resolve.
- Connector or infrastructure issues must be reported with the specific error, the attempted action, and what is still needed from the user. Resume automatically once the blocker is cleared.

## Quality Bar
Before finishing, verify all of the following:

- The business knowledge file is detailed enough to answer common customer questions about services, pricing logic, scope, process, and escalation.
- The style guide is detailed enough to reproduce consistent greetings, tone, structure, formatting, clarification language, closing habits, and multilingual behavior.
- Both files use the required section order and required item schema.
- Both files are clear enough that a human can manually add rules without changing the structure.
- Nothing in either file depends on undocumented assumptions.

## Completion Condition
Initialization is complete only when ALL of the following are true:

- Both target files exist.
- Neither file is in State B (Template). Every required agent-generated section contains at least one real, evidence-backed entry, or an explicit justified entry in `Known Unknowns` when the mailbox genuinely lacks signal for that section.
- No agent-generated item still reads `Not initialized yet`, `None yet`, or other placeholder wording from the template.
- `Source Evidence` fields point to specific Gmail threads or messages rather than `None yet`.
- Human Overrides sections are untouched.
- For a State C re-run, completion additionally requires that the full mailbox scan has actually been performed and that any new durable rules discovered have been merged in.

If any of these conditions is not met, initialization is not complete and you must continue working.

## Post-Bootstrap Rule
After initialization, `INIT.MD` must be ignored by the normal drafting workflow. Future draft generation should use only:

- `COMPANY_BUSINESS_KNOWLEDGE.MD`
- `EMAIL_REPLY_STYLE_GUIDE.MD`
- The live Gmail thread being handled
