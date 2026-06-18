# 领域文档

工程类 skills 在探索代码库时，应按本文件说明读取本仓库的领域文档。

## 探索前先读取这些文档

- 根目录的 **`CONTEXT.md`**；或
- 如果根目录存在 **`CONTEXT-MAP.md`**，读取它；它会指向每个 context 对应的 `CONTEXT.md`。只读取与当前主题相关的文件。
- **`docs/adr/`**：读取与你即将处理区域相关的 ADR。在 multi-context 仓库中，也要检查 `src/<context>/docs/adr/` 中的 context 级决策。

如果这些文件不存在，**静默继续**。不要把缺失当成问题，也不要预先建议创建。生产者 skill（`/grill-with-docs`）会在术语或决策真正被澄清后按需创建它们。

## 文件结构

Single-context 仓库（多数仓库）：

```text
/
|-- CONTEXT.md
|-- docs/adr/
|   |-- 0001-event-sourced-orders.md
|   `-- 0002-postgres-for-write-model.md
`-- src/
```

Multi-context 仓库（根目录存在 `CONTEXT-MAP.md`）：

```text
/
|-- CONTEXT-MAP.md
|-- docs/adr/                          <- 系统级决策
`-- src/
    |-- ordering/
    |   |-- CONTEXT.md
    |   `-- docs/adr/                  <- context 级决策
    `-- billing/
        |-- CONTEXT.md
        `-- docs/adr/
```

## 使用 glossary 中的词汇

当输出中需要命名领域概念时（例如 issue 标题、重构提案、假设、测试名称），使用 `CONTEXT.md` 中定义的术语。不要改用 glossary 明确避免的同义词。

如果你需要的概念还不在 glossary 中，这是一个信号：要么你正在创造项目并未使用的语言（需要重新考虑），要么确实存在文档缺口（记录给 `/grill-with-docs`）。

## 文档语言

项目文档默认使用中文维护，包括新增文档、现有文档更新、PRD、承担规格说明用途的 issue，以及 ADR。

已建立的英文专有名词、API 名称、命令、代码标识符、文件路径和 labels 保持不变，除非项目已经有对应的中文约定。

## 标出 ADR 冲突

如果你的输出与现有 ADR 冲突，必须明确指出，而不是静默覆盖：

> _Contradicts ADR-0007 (event-sourced orders) - but worth reopening because..._
