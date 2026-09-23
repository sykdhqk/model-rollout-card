# 模型上线卡

[English](README.md) · 支持在 [iPolloWork](https://github.com/Devin-AXIS/iPolloWork) 中使用

模型上线卡是一个离线 iPolloWork Skill，可把提供的模型上线材料整理为中英双语上线卡。它将策略、成本、测试、负责人和回退证据与未经证实的说法分开，帮助团队做出有依据的人工决策。

## 适用对象

当开发者效率、平台或治理团队准备向有限用户群引入模型，并需要一份可审阅记录来说明谁可以使用、已检查内容、可能成本和仍需确认事项时，可使用本 Skill。

## 功能

- 根据本地材料生成稳定的中英双语 Markdown 卡片。
- 使用四种就绪状态：`ready / 可上线`、`needs-confirmation / 需确认`、`blocked / 已阻塞`、`not-applicable / 不适用`。
- 将提供的证据与缺失的审批和测试结果区分开。
- 生成可执行的验收清单与回退章节。
- 不使用网络连接、账号、本地服务、可执行程序或厂商凭据。

## 工作流程

1. 准备 Markdown 材料，包含模型或功能、用户、访问策略、价格或额度说明、测试证据、负责人和回退方案。
2. 要求已安装的 Skill 阅读材料，并在同目录生成上线卡。
3. 与表中列出的负责人逐项审阅所有非“可上线”内容。
4. 将完成的卡片附到上线评审中；它不会修改厂商策略或生产设置。

## 输入与输出

输入为本地 Markdown 材料。输出为 Markdown 卡片，包含范围、访问与策略、用量与成本、就绪表、验收检查、回退和证据说明。缺失的材料会保持为待确认状态。

## 端到端示例

在 iPolloWork 项目中打开 `examples/grok-rollout-packet.md`，然后输入：

```text
Use Model Rollout Card on examples/grok-rollout-packet.md. Create grok-rollout-card.md beside it.
```

预期结果见 `examples/expected-rollout-card.md`：访问策略、预算审批和可复现测试输出均需确认；提供的回退路径可进入评审。

## 在 iPolloWork 中安装和使用

本包支持在 [iPolloWork](https://github.com/Devin-AXIS/iPolloWork) 中使用。

1. 从 Releases 下载 `model-rollout-card-1.0.0.ipollowork-plugin`。
2. 在 iPolloWork 中依次选择**扩展 → 插件 → 添加 → 文件**，选中安装包，核对名称、发布者 `sykdhqk`、版本 `1.0.0` 和一个 Skill 资源后安装。
3. 保持 Skill 启用。在本地项目任务中给出材料路径，并明确要求使用 **Model Rollout Card**。
4. 审阅生成的 Markdown，并将其与上线材料一起保存。
5. 如需本地 Skill 导入，解压 `model-rollout-card-1.0.0-skill.zip`，选择直接包含 `SKILL.md` 的文件夹；已有任务没有显示 Skill 时重新加载窗口。

## 构建和打包

仅重新构建产物时需要 Node.js 22+ 和系统 `zip` 命令。

```text
npm test
npm run package
```

Release 包含安装包、独立 Skill ZIP、源码 ZIP 和 `SHA256SUMS.txt`。将它们下载到同一目录后运行 `shasum -a 256 -c SHA256SUMS.txt`。

## 实测环境与限制

版本 1.0.0 面向 macOS arm64 上的 iPolloWork 0.50.12 和 OpenCode 引擎打包。它是一个 `source.trusted=false` 的普通声明式 Skill，不含权限。桌面验收会导入安装包、核对全部参考文件、运行示例并检查生成的卡片。Skill 只能评估提供的材料，不能核实实时模型访问、厂商价格、组织策略、厂商配置、命令结果或生产安全性。

## 常见问题

**可以启用模型吗？** 不可以，它只生成决策记录。

**可以估算成本吗？** 只有输入材料包含成本证据时才可以；否则会生成待确认项。

**可以替代上线评审吗？** 不可以，负责人必须审批未解决事项。
