---
name: ui-ux-pro-max-skill
description: "Bundle index for the UI/UX Pro Max skill suite. Use when an agent needs to discover the bundled design skills for UI/UX design intelligence, branding, banners, slides, design systems, Tailwind or shadcn/ui styling, logo design, icons, and social media creative workflows."
---

# UI/UX Pro Max Skill Bundle

Use this file as the bundle entrypoint when an agent scans `.ai/skills/ui-ux-pro-max-skill` directly.

Load the focused skill instead of this bundle whenever the task intent is clear:

- `../ui-ux-pro-max/SKILL.md` for design intelligence, palettes, typography, UX guidelines, charts, and stack recommendations.
- `../design/SKILL.md` for logo, icon, CIP, mockup, social image, and broad creative design workflows.
- `../banner-design/SKILL.md` for social, ads, website hero, creative, and print banners.
- `../ui-styling/SKILL.md` for Tailwind CSS, shadcn/ui, Radix UI, accessible components, themes, and responsive styling.
- `../brand/SKILL.md` for brand voice, visual identity, messaging, guidelines, and asset management.
- `../slides/SKILL.md` for strategic HTML presentations and Chart.js slide layouts.
- `../design-system/SKILL.md` for design tokens, component specs, CSS variables, and token architecture.

Keep the direct symlinks in `.ai/skills/` as the primary discovery path for agents that scan one skill per direct child folder.
