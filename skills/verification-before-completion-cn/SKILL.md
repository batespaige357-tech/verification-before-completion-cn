---
name: verification-before-completion-cn
description: Chinese-adapted evidence-before-claims workflow for 完成前验证、交付核对、测试结果确认. Use when about to claim work is complete, fixed, or passing, before committing or creating PRs - requires running verification commands and confirming output before making any success claims; evidence before assertions always
---

# Verification Before Completion

## Overview

**Core principle:** Evidence before claims, always.

**Violating the letter of this rule is violating the spirit of this rule.**

## The Iron Law

```
NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE
```

If you haven't run the verification command in this message, you cannot claim it passes.

## The Gate Function

```
BEFORE claiming any status or expressing satisfaction:

1. IDENTIFY: What command proves this claim?
2. RUN: Execute the FULL command (fresh, complete)
3. READ: Full output, check exit code, count failures
4. VERIFY: Does output confirm the claim?
   - If NO: State actual status with evidence
   - If YES: State claim WITH evidence
5. ONLY THEN: Make the claim

Skip any step = lying, not verifying
```

## Common Failures

| Claim | Requires | Not Sufficient |
|-------|----------|----------------|
| Tests pass | Test command output: 0 failures | Previous run, "should pass" |
| Linter clean | Linter output: 0 errors | Partial check, extrapolation |
| Build succeeds | Build command: exit 0 | Linter passing, logs look good |
| Bug fixed | Test original symptom: passes | Code changed, assumed fixed |
| Regression test works | Red-green cycle verified | Test passes once |
| Agent completed | VCS diff shows changes | Agent reports "success" |
| Requirements met | Line-by-line checklist | Tests passing |

## Red Flags - STOP

- Using "should", "probably", "seems to"
- Expressing satisfaction before verification ("Great!", "Perfect!", "Done!", etc.)
- About to commit/push/PR without verification
- Trusting agent success reports
- Relying on partial verification
- Thinking "just this once"
- Tired and wanting work over
- **ANY wording implying success without having run verification**

## Rationalization Prevention

| Excuse | Reality |
|--------|---------|
| "Should work now" | RUN the verification |
| "I'm confident" | Confidence ≠ evidence |
| "Just this once" | No exceptions |
| "Linter passed" | Linter ≠ compiler |
| "Agent said success" | Verify independently |
| "I'm tired" | Exhaustion ≠ excuse |
| "Partial check is enough" | Partial proves nothing |
| "Different words so rule doesn't apply" | Spirit over letter |

## Key Patterns

**Tests:**
```
✅ [Run test command] [See: 34/34 pass] "All tests pass"
❌ "Should pass now" / "Looks correct"
```

**Regression tests (TDD Red-Green):**
```
✅ Write → Run (pass) → Revert fix → Run (MUST FAIL) → Restore → Run (pass)
❌ "I've written a regression test" (without red-green verification)
```

**Build:**
```
✅ [Run build] [See: exit 0] "Build passes"
❌ "Linter passed" (linter doesn't check compilation)
```

**Requirements:**
```
✅ Re-read plan → Create checklist → Verify each → Report gaps or completion
❌ "Tests pass, phase complete"
```

**Agent delegation:**
```
✅ Agent reports success → Check VCS diff → Verify changes → Report actual state
❌ Trust agent report
```

## When To Apply

**ALWAYS before:**
- ANY variation of success/completion claims
- ANY expression of satisfaction
- ANY positive statement about work state
- Committing, PR creation, task completion
- Moving to next task
- Delegating to agents

**Rule applies to:**
- Exact phrases
- Paraphrases and synonyms
- Implications of success
- ANY communication suggesting completion/correctness


## 中文交付适配 — verification-before-completion-cn

本节为独立社区补充，保留上游五步验证关卡与证据标准，不代表 Superpowers 官方。

### 每一句结论都要限定范围

用中文区分：已验证、失败、未验证、受阻。只在有新证据时使用“通过／已修复／已上线”等结论；不能用“基本完成”“理论上没问题”掩盖缺口。

每项重要结论可以简短写成：结论 → 验证动作 → 实际观察 → 适用范围。保留命令、路径、错误码、版本和退出码原文；中文说明不替换原始证据。无需为了简单任务机械输出四列大表。

- 检查命令启动不等于完成。仍在运行时报告进行中，完成后读取退出状态和相关输出。
- 文件保存／本地提交／推送成功／远端部署生效是不同事实，验证了哪一步就只声称哪一步。
- 一个尺寸或环境通过，不延伸为所有设备或环境通过。格式检查不等于真实功能测试，测试通过不等于全部需求满足。
- 证据引用实际路径或可核实的结果，不编造日志、数量、时间或截图。旧结果明确标明，不能作为本次新状态的证明。

### 用户限制仍然有效

验证关卡不扩大任务授权。用户没有要求前端编译时，不为证明完成而自行运行 build；可以继续获准的静态或功能检查，并明确“未编译”，不得写“构建通过”。也不能借验证之名发布、删数据、安装依赖或改生产配置。

验证受阻时说明缺少什么证据、已知事实与未验证项。敏感输出只保留必要结构与错误信息，不在报告里暴露凭据。用户明确限制某项检查时，报告该限制，不绕过。
