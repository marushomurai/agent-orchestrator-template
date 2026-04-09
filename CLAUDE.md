# Agent Orchestration Template

このリポは **オーケストレーション・エージェントプール** のひな型。**詳細なワークフロー・ディレクトリ・マトリクス・YAML例**: [`.claude/agents/orchestrator.md`](.claude/agents/orchestrator.md) と [`.claude/agents/_template.md`](.claude/agents/_template.md)

## 憲法（要約）

- タスクは **プール覆盖率** に基づき既存 / 統合 / 新規エージェントを選ぶ  
- **事前定義の抽象エージェントだけに頼らない** — 要件から具体化する  
- 実行後は `manifests/` のメトリクス更新。条件達成で `elite/` へ  

## クイックリファレンス

| 状況 | アクション |
|------|------------|
| 新規タスク | `pool/` をスキャンし覆盖率計算 |
| 90%+ 一致 | 既存エージェント |
| 60–90% | 統合エージェント作成 |
| <60% | 特化エージェント新規 |

## Rule split

- テンプレ注入用の長文ブロックは **`CLAUDE.md` に残さない** — このファイルは入口のみ。フル手順は `.claude/agents/` 側を更新する
