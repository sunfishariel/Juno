# AI PRD · Juno

> Module 3 · Harness / AI PRD. The AI product requirements doc specifying all six harness surfaces, built with the **M3 · AI PRD Builder** (archetype and starting settings from the **M3 · Harness Architecture Decider**). Paste the tool's markdown over this file.

_____

## Problem & user

RocketShip PMs need this handled: Juno compares PRDs with dependencies on each other, to identify risks and assumptions.. Juno does this inside limits a human set on purpose, and defends every call it makes.

## The harness

| Surface | Specification |
|---|---|
| 01 Context | Documents in the user's authenticated SharePoint, which refresh when SharePoint does. |
| 02 Tools | read_doc(doc_id) — READ search_reference(query) — READ compare_doc(doc_a, doc_b) — READ draft_priority(item_id, priority, rationale) — DRAFT |
| 03 Loop | One pass for now. |
| 04 Memory | Memory is persisted for the duration of the project, across the team. |
| 05 Permissions | read confirm · draft confirm · write confirm · send blocked |
| 06 Verification | Every priority cites the strategy or roadmap document. |

## 01 Context · Data Requirements

**Required sources, and exclusions**

Documents in the user's authenticated SharePoint, which refresh when SharePoint does. Additionally, the Product Strategy One-Pager, and Product Roadmap.

**How fresh must it be**

Every time the tool is evoked, it should refresh the sources based on the status of the SharePoint. If a source is unreachable, ask the user to manually refresh by closing and reopening the tool.

## 02 Tools · System Capabilities

**The verb list**

read_doc(doc_id) — READ
search_reference(query) — READ
compare_doc(doc_a, doc_b) — READ
draft_priority(item_id, priority, rationale) — DRAFT

**Deliberate omissions**

The tool will not have the ability to edit documents, nor see/access any documents that the user is not authenticated for.

## 03 Loop · AI Costs & Latency

**Turn ceiling and escalation**

One pass for now.

**Latency and cost target**

Answers back in under 20 seconds.

## 04 Memory · Data Requirements

**What persists, at what scope**

Memory is persisted for the duration of the project, across the team.

**Expiry and write rules**

User corrections are accepted and outranks the model output.

## 05 Permissions · AI Risks & Mitigations

**The permission tier**

| Side-effect class | Tier |
|---|---|
| read | confirm |
| draft | confirm |
| write | confirm |
| send | blocked |

**Justification**

It cannot access documents that have not explicitly been added to the tool. It cannot directly edit any documents unless the user allows it to.

## 06 Verification · AI Testing & Measurement

**The check before output ships**

Every priority cites the strategy or roadmap document.

**Failure behaviour**

Uncited priorities are returned labelled unverified, for human review and verification.

## Eval plan

_Stub. Module 6 fills this in: golden set, pass thresholds, and regression cadence for the verification gate above._

## Out of scope

Any capability not in the verb list above, and any action tiered `blocked`. Both are decisions on the record, not omissions.
