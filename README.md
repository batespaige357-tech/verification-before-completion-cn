# Verification Before Completion CN

**先拿证据，再说完成。**

基于 [obra/superpowers 的 verification-before-completion](https://github.com/obra/superpowers/tree/main/skills/verification-before-completion) 的小幅中文适配。独立社区版本，非官方。

## 保留什么

完整保留上游正文：识别验证动作、执行、读取输出、核对结论，再作完成声明。保留测试、修复、构建、回归与需求检查的证据标准，以及常见误判提醒。

## 只补这些

- 中文报告分清“已验证／失败／未验证／受阻”。
- 避免把已保存说成已上线，把单一环境通过说成全部通过。
- 原始命令、退出码与错误保持原文，中文解释不替代证据。
- 验证仍尊重用户限制：没有要求前端编译时，不自行 build，也不声称构建通过。

## 安装与使用

```bash
npx skills add batespaige357-tech/verification-before-completion-cn --skill verification-before-completion-cn
```

对助手说“用 verification-before-completion-cn 核对这次交付”；Codex 可输入 `$verification-before-completion-cn`。也可把 `skills/verification-before-completion-cn` 整个目录放到助手的技能目录。

这是验证工作流指令，不自带测试框架或扫描工具；实际检查使用项目已有且获准的能力。没有额外脚本、示例网页或效果截图。

## 来源与验证边界

沿用 MIT，保留 Jesse Vincent 版权及完整许可证。具体提交与修改见 [CHANGES.md](CHANGES.md)。

已检查原正文完整保留、UTF-8、技能格式和本地引用；尚未做真实助手行为盲测，不保证模型每次遵循，也没有效率或修复率成绩。没有运行前端编译。
