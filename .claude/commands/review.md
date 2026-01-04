---
description: コードレビュアーを呼び出してコードレビューを実行する
argument-hint: [ファイルパス（省略可）]
allowed-tools: Bash(git diff:*), Bash(git status:*), Read, Glob, Grep
---

# コードレビュー起動

code-reviewer SubAgentを使用して、コードレビューを実行してください。

## 対象
$ARGUMENTS

引数が指定されていない場合は、現在の変更（git diff）をレビューしてください。

## 事前確認

```bash
git status
git diff --staged
git diff
```

## 実行手順

1. 変更内容を把握
2. レビュー観点に基づいて評価
3. 指摘事項を整理
4. 総合評価を決定

## 出力

レビュー結果を報告し、コミット可否の判断を提示してください。

- **LGTM**: コミット可能
- **要修正**: 修正後に再レビュー
- **要議論**: 追加の議論が必要
