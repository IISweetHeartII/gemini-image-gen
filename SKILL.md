---
name: gemini-image-gen
description: Generate and edit images via Google Gemini API. Supports Gemini native image generation and Imagen 3. Batch generation with HTML gallery. Zero dependencies — pure Python stdlib.
homepage: https://github.com/IISweetHeartII/gemini-image-gen
metadata:
  {"openclaw": {"emoji": "🎨", "requires": {"bins": ["python3"], "env": ["GEMINI_API_KEY"]}, "primaryEnv": "GEMINI_API_KEY"}}
---

# Gemini Image Gen

Generate images via the Google Gemini API. Supports two engines:

- **gemini** (default) — Native Gemini image generation (`gemini-2.5-flash-image`). Supports both generation AND editing.
- **imagen** — Google Imagen 3 (`imagen-3.0-generate-002`). High-quality image generation.

Zero external dependencies — pure Python stdlib only.

## Generate images

```bash
# Default: Gemini native, 4 random prompt images
python3 {baseDir}/scripts/gen.py

# Custom prompt
python3 {baseDir}/scripts/gen.py --prompt "a cyberpunk cat riding a neon motorcycle through Tokyo at night"

# Batch generation
python3 {baseDir}/scripts/gen.py --count 8 --prompt "serene mountain landscape at golden hour"

# Use Imagen 3 engine
python3 {baseDir}/scripts/gen.py --engine imagen --count 4

# Custom aspect ratio (Imagen 3)
python3 {baseDir}/scripts/gen.py --engine imagen --aspect 16:9

# Custom output directory
python3 {baseDir}/scripts/gen.py --out-dir ./my-images
```

## Edit existing images (Gemini native only)

```bash
# Edit an image with a text prompt
python3 {baseDir}/scripts/gen.py --edit path/to/image.png --prompt "change the background to a sunset beach"

# Style transfer
python3 {baseDir}/scripts/gen.py --edit photo.jpg --prompt "convert to watercolor painting style"
```

## Options

| Flag | Default | Description |
|------|---------|-------------|
| `--prompt` | (random) | Text prompt. Omit for random creative prompts |
| `--count` | 4 | Number of images to generate |
| `--engine` | gemini | Engine: `gemini` or `imagen` |
| `--model` | (auto) | Model override. Default: `gemini-2.5-flash-image` or `imagen-3.0-generate-002` |
| `--edit` | | Path to input image for editing (Gemini engine only) |
| `--aspect` | 1:1 | Aspect ratio for Imagen: `1:1`, `16:9`, `9:16`, `4:3`, `3:4` |
| `--out-dir` | (auto) | Output directory |

## Output

- `*.png` images
- `prompts.json` (prompt-to-file mapping)
- `index.html` (thumbnail gallery with dark theme)

## API Key

Requires `GEMINI_API_KEY` environment variable. Get one free at https://aistudio.google.com/apikey
