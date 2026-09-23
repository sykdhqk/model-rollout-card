---
name: model-rollout-card
description: Use when a team needs to turn supplied AI model availability, policy, pricing, test, or rollout notes into a bilingual launch card and approval-ready checklist.
---

# Model Rollout Card / 模型上线卡

## Input / 输入

Read a local Markdown packet. It should identify the model or feature, intended users, access policy, known pricing or quota facts, tested workflow, evidence, owner, and rollback path. Do not fetch a live vendor console or assume a model is enabled.

## Workflow / 工作流程

1. Read the packet and `references/decision-rules.md`.
2. Preserve supplied facts with their evidence. Label a missing fact as `needs-confirmation / 需确认`; do not infer entitlement, model availability, cost, security approval, or test success.
3. Build the card using `references/output-format.md`: scope, access and policy, usage and cost, acceptance checks, rollback, and a bilingual decision table.
4. Classify each readiness item as `ready / 可上线`, `needs-confirmation / 需确认`, `blocked / 已阻塞`, or `not-applicable / 不适用`.
5. Save the result beside the packet as `<packet-name>-rollout-card.md` unless the user names an output file.

## Output / 输出

Produce a concise bilingual Markdown card. It must state that it is based only on supplied material, identify the owner for each unresolved item, and give a concrete next check. It prepares a human rollout decision; it does not change a model policy, spend limit, production routing, or vendor setting.

## Dependencies / 依赖

No network, account connection, executable, local service, or external dependency.
