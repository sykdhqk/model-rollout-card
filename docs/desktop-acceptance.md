# Desktop acceptance / 桌面验收

## Environment / 环境

- iPolloWork 0.50.12 on macOS arm64
- Package: `model-rollout-card-1.0.0.ipollowork-plugin`
- Mode: **Extensions → Add → File → Install plugin**

## Import result / 导入结果

The installer preview showed one Skill, zero apps, commands, MCP servers, and agents. iPolloWork completed its declarative safety check and displayed the plugin as installed and enabled.

安装预览显示 1 个 Skill、0 个应用、命令、MCP 和 Agent。iPolloWork 通过声明式安全检查，并将插件显示为已安装、已启用。

## Invocation result / 调用结果

In an iPolloWork project workspace, the task loaded `model-rollout-card`, read both bundled references and a local rollout packet, then created `model-rollout-card-output.md`.

The generated bilingual card preserved the supplied facts and marked the absent policy evidence, monthly budget approval, model-availability evidence, and test transcript as `needs-confirmation / 需确认`. It did not claim a live policy change or model availability.

在 iPolloWork 项目工作区中，任务加载了 `model-rollout-card`，读取了两个随包参考文件和本地上线材料，然后创建 `model-rollout-card-output.md`。生成的中英双语卡片保留了所提供的事实，并将缺失的策略证据、月度预算批准、模型可用性证据和测试记录标记为 `needs-confirmation / 需确认`；未声称已修改在线策略或模型可用性。
