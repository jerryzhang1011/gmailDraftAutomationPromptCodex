# One-Time Bootstrap Specification for Gmail Reply Intelligence

## Status
- This file is bootstrap-only.
- Use this file exactly once to initialize the project.
- Do not include this file in the normal day-to-day drafting workflow after initialization is complete.

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
- The two target files if they already exist.

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

1. Open and read the existing `COMPANY_BUSINESS_KNOWLEDGE.MD` and `EMAIL_REPLY_STYLE_GUIDE.MD` if they already exist.
2. Preserve all human-owned sections and any clearly human-authored notes.
3. Use the Gmail connector to shortlist high-signal Primary mailbox messages.
4. Expand promising items into full threads and study them for durable business facts and writing patterns.
5. Extract normalized, evidence-backed rules into the two target files.
6. Deduplicate overlapping observations.
7. Place unresolved or conflicting evidence in `Known Unknowns`.
8. Update the `Evidence Index` with concise references.
9. Verify that no content depends on `INIT.MD` for future runtime drafting.

## Quality Bar
Before finishing, verify all of the following:

- The business knowledge file is detailed enough to answer common customer questions about services, pricing logic, scope, process, and escalation.
- The style guide is detailed enough to reproduce consistent greetings, tone, structure, formatting, clarification language, closing habits, and multilingual behavior.
- Both files use the required section order and required item schema.
- Both files are clear enough that a human can manually add rules without changing the structure.
- Nothing in either file depends on undocumented assumptions.

## Completion Condition
Initialization is complete only when both target files exist in their long-lived form and can support future Gmail draft generation without requiring `INIT.MD`.

## Post-Bootstrap Rule
After initialization, `INIT.MD` must be ignored by the normal drafting workflow. Future draft generation should use only:

- `COMPANY_BUSINESS_KNOWLEDGE.MD`
- `EMAIL_REPLY_STYLE_GUIDE.MD`
- The live Gmail thread being handled
