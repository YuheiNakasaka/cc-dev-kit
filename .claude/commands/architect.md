---
description: アーキテクトを呼び出して実装方針を立案する
argument-hint: [機能の説明]
---

# アーキテクト起動

architect SubAgentを使用して、以下の機能の実装方針を立案してください。

## 対象機能
$ARGUMENTS

## 実行手順

1. 要件を分析し、不明点があれば`AskUserQuestion`で確認
2. 既存コードベースを調査
3. 実装方針を立案
4. 設計書を`.claude/tmp/design/`に作成
5. 設計レビューの準備

## 出力

設計書を作成し、設計レビュー（`/design-review`）の実施を推奨してください。
