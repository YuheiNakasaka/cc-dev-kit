---
description: レビュー確認付きでコミットを作成する
argument-hint: [コミットメッセージ]
allowed-tools: Bash(git add:*), Bash(git commit:*), Bash(git status:*), Bash(git diff:*)
---

# レビュー確認付きコミット

コードレビューの実施状況を確認してからコミットを作成します。

## コミットメッセージ
$ARGUMENTS

## 実行手順

### 1. 変更内容の確認

```bash
git status
git diff --staged
```

### 2. レビュー確認

コードレビューは実施済みですか？

- 実施済みの場合: コミットを作成
- 未実施の場合: `/review` でレビューを実施することを推奨

### 3. コミット作成

レビュー実施済み、または未実施でも続行する場合:

```bash
git add -A
git commit -m "$ARGUMENTS"
```

## 注意事項

- レビュー未実施の場合は警告を表示
- 強制的にブロックはしない（開発者の判断を尊重）
- 小さな変更や自明な修正はレビューをスキップ可能

## 推奨フロー

```
コード変更 → /review → 修正 → /commit "メッセージ"
```
