# Playwright MCPルール

## スクリーンショットのリサイズ（必須）

Playwright MCPでスクリーンショットを撮影した場合、Claude Codeで利用する前に必ずImageMagickの`magick`コマンドでリサイズすること。

**理由**: 画像サイズが大きすぎるとClaude Codeがクラッシュする可能性がある。

## リサイズコマンド例

```bash
# 幅1024pxにリサイズ（アスペクト比維持）
magick input.png -resize 1024x output.png

# 最大幅・高さを指定（アスペクト比維持）
magick input.png -resize 1024x768\> output.png

# 品質を指定してJPEGに変換
magick input.png -resize 1024x -quality 85 output.jpg
```

## 推奨ワークフロー

1. Playwright MCPでスクリーンショットを撮影
2. `magick`でリサイズ（幅1024px推奨）
3. リサイズ後の画像をClaude Codeで分析

## 一時ファイルの保存先
スクリーンショットは `.claude/tmp/` に保存すること。
