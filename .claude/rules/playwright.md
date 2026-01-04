# Playwright MCP Rules

## Screenshot Resize (Required)

When taking screenshots with Playwright MCP, always resize with ImageMagick's `magick` command before using in Claude Code.

**Reason**: Large images may crash Claude Code.

## Resize Command Examples

```bash
# Resize to 1024px width (maintain aspect ratio)
magick input.png -resize 1024x output.png

# Specify max width/height (maintain aspect ratio)
magick input.png -resize 1024x768\> output.png

# Convert to JPEG with quality setting
magick input.png -resize 1024x -quality 85 output.jpg
```

## Recommended Workflow

1. Take screenshot with Playwright MCP
2. Resize with `magick` (1024px width recommended)
3. Analyze resized image in Claude Code

## Temp File Location
Save screenshots to `.claude/tmp/`.
