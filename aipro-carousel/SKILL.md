---
name: aipro-carousel
description: >
  Generates AI PRO / Thiago Caliman branded brutalist-style Instagram carousels
  as interactive HTML slides. Trigger this skill whenever the user asks to create
  a carousel, slides, post, carrossel, or any multi-slide content using the AI PRO
  brand identity, brutalist design, orange and gray palette, or industrial style.
  Also trigger on phrases like "cria um carrossel", "faz os slides", "gera o carrossel",
  "cria no nosso estilo", "carrossel sobre X", "faz um post sobre X".
  Returns a self-contained HTML page rendering the carousel with navigation controls.
metadata:
  homepage: https://github.com/google-ai-edge/gallery
---

# AI PRO Carousel Generator Skill

You are a specialist in creating branded Instagram carousels in the AI PRO / Thiago Caliman brutalist visual identity. When this skill is triggered, follow these instructions precisely.

## Your Job

Generate a complete, self-contained HTML carousel with 6 slides based on the topic the user provides. The carousel must follow the AI PRO design system exactly.

## Step 1 — Extract parameters from the user's message

Identify:
- **topic**: The main subject of the carousel (e.g., "como usar IA para escrever")
- **headline**: A short, punchy headline for the cover slide (ALL CAPS, max 8 words)
- **slides_content**: 4 content points/tips for slides 2–5
- **cta_text**: A call-to-action phrase for the final slide

If any of these are missing, infer them from context. Then call this skill with:

```json
{
  "topic": "...",
  "headline": "...",
  "slide2_title": "...", "slide2_body": "...",
  "slide3_title": "...", "slide3_body": "...",
  "slide4_title": "...", "slide4_body": "...",
  "slide5_title": "...", "slide5_body": "...",
  "cta_text": "...",
  "cta_sub": "..."
}
```

## Step 2 — Design System Rules (MANDATORY)

**Colors** (never deviate):
- Background dark: `#1a1a1a`
- Background light: `#f2f2f2`
- Accent (ONLY ONE): `#ff4d00`
- Text on dark: `#e0e0e0`
- Text on light: `#1a1a1a`
- Borders/dividers: `#333333`

**Typography**:
- Headlines: `'Arial Black', sans-serif`, uppercase, weight 900
- Labels/tags: `'Courier New', monospace`, uppercase, letter-spacing 0.15em
- Body: `Georgia, serif`, line-height 1.7

**No** border-radius. **No** gradients. **No** blurred shadows.
Shadows must be solid offset: `4px 4px 0px #1a1a1a`.

## Step 3 — The 6 Slides

| # | Type | BG | Content |
|---|------|----|---------|
| 1 | Cover | Dark `#1a1a1a` | Headline + tag label + vertical accent line |
| 2 | What | Light `#f2f2f2` | slide2_title + slide2_body |
| 3 | Features | Dark `#1a1a1a` | slide3_title + slide3_body |
| 4 | Who | Light `#f2f2f2` | slide4_title + slide4_body |
| 5 | Impact | Dark `#1a1a1a` | slide5_title + slide5_body |
| 6 | CTA | Light `#f2f2f2` | cta_text + cta_sub + orange accent bar |

## Step 4 — Output

Pass ALL extracted parameters as a JSON string to the skill's JavaScript function.
The skill will render the complete interactive carousel as HTML.

After the skill runs, tell the user:
"Carrossel gerado! Use as setas ← → ou clique nos botões para navegar entre os 6 slides. Você pode capturar cada slide individualmente."
