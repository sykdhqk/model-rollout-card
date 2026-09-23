# Model Rollout Card

[简体中文](README.zh-CN.md) · Supports [iPolloWork](https://github.com/Devin-AXIS/iPolloWork)

Model Rollout Card is an offline iPolloWork Skill that converts supplied model-rollout material into a bilingual launch card. It keeps policy, cost, testing, ownership, and rollback evidence separate from claims so a team can make an informed human decision.

## Who it helps

Use it when a developer-productivity, platform, or governance team is introducing a model to a limited group and needs one reviewable record of who may use it, what was checked, what it may cost, and what still requires confirmation.

## Features

- Produces a stable bilingual Markdown card from a local packet.
- Tracks four readiness states: `ready / 可上线`, `needs-confirmation / 需确认`, `blocked / 已阻塞`, and `not-applicable / 不适用`.
- Separates supplied evidence from missing approvals and test results.
- Creates a practical acceptance checklist and rollback section.
- Uses no network connection, account, local service, executable, or vendor credentials.

## Workflow

1. Prepare a Markdown packet with the model or feature, users, access policy, pricing or quota notes, test evidence, owner, and rollback plan.
2. Ask the installed Skill to read that packet and create a rollout card beside it.
3. Review every non-ready row with the listed owner.
4. Attach the finished card to the rollout review; it does not change any vendor policy or production setting.

## Inputs and outputs

The input is a local Markdown packet. The output is a Markdown card with scope, access and policy, usage and cost, a readiness table, acceptance checks, rollback, and an evidence note. Missing material remains marked for confirmation.

## End-to-end example

Open `examples/grok-rollout-packet.md` in an iPolloWork project and ask:

```text
Use Model Rollout Card on examples/grok-rollout-packet.md. Create grok-rollout-card.md beside it.
```

The expected result is shown in `examples/expected-rollout-card.md`: access policy, budget approval, and repeatable test output require confirmation; the supplied rollback route is ready for review.

## Install and use in iPolloWork

This package supports [iPolloWork](https://github.com/Devin-AXIS/iPolloWork).

1. Download `model-rollout-card-1.0.0.ipollowork-plugin` from Releases.
2. In iPolloWork, choose **Extensions / 扩展 → Plugins / 插件 → Add / 添加 → File / 文件**, select the package, inspect its name, publisher `sykdhqk`, version `1.0.0`, and one Skill resource, then install it.
3. Keep the Skill enabled. In a local project task, provide a packet path and explicitly ask to use **Model Rollout Card**.
4. Review and save the generated Markdown with the rollout material.
5. For local-Skill import, unzip `model-rollout-card-1.0.0-skill.zip` and select the folder that directly contains `SKILL.md`. Reload the window if an existing task does not show the Skill.

## Build and package

Node.js 22+ and the system `zip` command are needed only to rebuild distribution files.

```text
npm test
npm run package
```

The release includes the installer, a direct Skill ZIP, a source ZIP, and `SHA256SUMS.txt`. Download them into one directory and run `shasum -a 256 -c SHA256SUMS.txt`.

## Tested environment and limits

Version 1.0.0 is packaged for iPolloWork 0.50.12 on macOS arm64 with the OpenCode engine. It is a single ordinary declarative Skill with `source.trusted=false` and no permissions. Desktop acceptance imports the installer, verifies all reference files, runs the example, and checks its generated card. The Skill only evaluates supplied material: it cannot verify live model access, provider pricing, organization policy, vendor configuration, a command result, or production safety.

## FAQ

**Can it enable a model?** No. It creates a decision record only.

**Can it estimate cost?** Only when the supplied packet contains cost evidence; otherwise it creates a confirmation item.

**Can it replace a rollout review?** No. A human owner must approve unresolved items.
