# Claude Code 開発基盤

このリポジトリはClaude Codeを中心としたチーム開発のためのテンプレートです。

## 概要

このテンプレートを他のプロジェクトにコピーして使用することで、以下の開発基盤が整います:

- 役割分担によるSubAgents（アーキテクト、レビュアー、各種開発者）
- TDD（テスト駆動開発）のサポート
- コードレビューの仕組み
- 一貫したルールとワークフロー

---

## 開発フロー

### 推奨フロー

```
1. /architect [機能説明]     → 実装方針の立案
2. /design-review            → 設計レビュー
3. /tdd [機能説明]           → TDDで実装（テスト → 実装 → リファクタ）
4. /review                   → コードレビュー
5. /commit "メッセージ"       → コミット
```

### TDD（テスト駆動開発）

テストファースト開発を推奨します。`/tdd` コマンドで開始できます。

1. **Red**: テストを先に書く（失敗することを確認）
2. **Green**: テストを通す最小限の実装
3. **Refactor**: コードを改善（テストは維持）

### コミット規約

- 1機能ごとにこまめにcommit
- commit前のコードレビューを推奨
- コミット時に警告が表示されますが、ブロックはしません

---

## ディレクトリ構造

```
.claude/
├── CLAUDE.md              # このファイル
├── settings.json          # Claude Code設定（Hooks、権限）
├── .mcp.json              # MCP設定（API Key等を含む場合は.gitignore推奨）
├── tmp/                   # 一時ファイル（git管理外）
│   └── design/            # 設計書
├── rules/                 # 自動適用ルール
│   ├── general.md         # 一般ルール
│   ├── tdd.md             # TDDルール
│   ├── commit.md          # コミットルール
│   ├── playwright.md      # Playwrightルール
│   ├── ask-user.md        # 確認ルール
│   └── tmp-files.md       # 一時ファイルルール
├── agents/                # SubAgents
│   ├── architect/         # アーキテクト
│   ├── design-reviewer/   # 設計レビュアー
│   ├── code-reviewer/     # コードレビュアー
│   ├── api-developer/     # API開発者
│   ├── frontend-developer/# フロントエンド開発者
│   ├── db-designer/       # DB設計者
│   ├── ui-designer/       # UIデザイナー
│   ├── modeler/           # モデリング担当
│   ├── tdd-test-writer/   # TDDテスト作成者
│   └── tdd-implementer/   # TDD実装者
├── skills/                # Skills
│   ├── ui-check/          # UI確認スキル
│   └── external-systems/  # 外部システム連携
└── commands/              # スラッシュコマンド
    ├── architect.md       # /architect
    ├── design-review.md   # /design-review
    ├── review.md          # /review
    ├── tdd.md             # /tdd
    └── commit.md          # /commit
```

---

## コマンド一覧

| コマンド | 説明 |
|---------|------|
| `/architect [説明]` | アーキテクトを呼び出して実装方針を立案 |
| `/design-review` | 設計レビューを実行 |
| `/review` | コードレビューを実行 |
| `/tdd [説明]` | TDD開発フローを開始 |
| `/commit "メッセージ"` | レビュー確認付きコミット |

---

## SubAgents

### 設計フェーズ
- **architect**: 実装方針の立案、技術選定
- **design-reviewer**: 設計方針のレビュー、承認
- **modeler**: ドメインモデリング、業務設計

### 実装フェーズ
- **api-developer**: Rails API開発
- **frontend-developer**: React/ViewComponent開発
- **db-designer**: スキーマ設計、マイグレーション
- **ui-designer**: UIデザイン、スタイリング

### レビューフェーズ
- **code-reviewer**: commit前のコードレビュー

### TDDフェーズ
- **tdd-test-writer**: テストの作成（Redフェーズ）
- **tdd-implementer**: 最小限の実装（Greenフェーズ）

---

## MCP（Model Context Protocol）

MCP設定は`.claude/.mcp.json`に記述します。

### 初期設定（Context7 API Key）

Context7を使用するには、API Keyの設定が必要です。

1. [Context7](https://context7.com/)でAPI Keyを取得
2. `.claude/.mcp.json`のcontext7セクションにenv設定を追加:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"],
      "env": {
        "CONTEXT7_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

**注意**: API Keyを含む`.mcp.json`は`.gitignore`に追加するか、`settings.local.json`で管理してください。

### 利用可能なMCPサーバー

#### Playwright
UIのスクリーンショット撮影、ブラウザ操作。

```
mcp__playwright__browser_navigate
mcp__playwright__browser_screenshot
```

**注意**: スクリーンショットは必ず`magick`でリサイズしてから使用。

#### Chrome DevTools
ブラウザのDevTools操作。

#### Context7
OSS（Rails、ViewComponentなど）の最新ドキュメントにアクセス。

```
Context7を使って、ViewComponentの最新ドキュメントを確認して
```

---

## Git/GitHub操作

- `gh`コマンドを使用（MCP経由ではない）
- PRの作成: `gh pr create`
- Issue操作: `gh issue list`, `gh issue create`

---

## 一時ファイル

作業中に作成する一時ファイルは`.claude/tmp/`に保存してください:

- 設計書: `.claude/tmp/design/`
- スクリーンショット: `.claude/tmp/screenshots/`
- 調査メモ: `.claude/tmp/research/`

---

## ルール参照

詳細なルールは`.claude/rules/`を参照:
- @rules/general.md - 一般ルール
- @rules/tdd.md - TDDルール
- @rules/commit.md - コミットルール
- @rules/playwright.md - Playwrightルール
- @rules/ask-user.md - 確認ルール
- @rules/tmp-files.md - 一時ファイルルール
