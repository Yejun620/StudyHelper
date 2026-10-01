# StudyHelper

AI-powered study assistant that turns lecture PDFs into concept notes, summaries, and practice quizzes using the Claude API.

> **Status:** 🚧 Under active development. The project skeleton is set up; core features are being built.

## Overview

Upload your lecture notes (for example, an AMS 310 probability & statistics PDF) and StudyHelper generates:

- **Concept notes** – definitions, key formulas, intuition, and examples, with source page references
- **Summary** – a TL;DR, section-by-section bullets, and exam tips
- **Quiz** – multiple-choice, short-answer, and true/false questions with explanations and difficulty levels
- **Flashcards** – flip cards built from the extracted concepts

Math is rendered with KaTeX, so formulas in your notes stay readable.

## How it works

```
Browser ── upload PDF ──▶ Next.js API route ──▶ Claude API
   ▲                         │  PDF sent as a document block
   │                         │  3 parallel calls: concepts / summary / quiz
   └── structured results ◀──┘  validated against Zod schemas
```

Claude returns structured JSON (via tool use), which is validated with Zod before it reaches the UI.

## Tech stack

- [Next.js](https://nextjs.org) (App Router) + TypeScript
- [Tailwind CSS](https://tailwindcss.com)
- [Anthropic SDK](https://github.com/anthropics/anthropic-sdk-typescript) (Claude API)
- [Zod](https://zod.dev) for schema validation
- [react-markdown](https://github.com/remarkjs/react-markdown) + [KaTeX](https://katex.org) for math rendering
- [Framer Motion](https://www.framer.com/motion/), [lucide-react](https://lucide.dev), [next-themes](https://github.com/pacocoursey/next-themes) for UI

## Getting started

Requirements: Node.js 20+ (developed on Node 24 LTS) and npm.

```bash
git clone https://github.com/Yejun620/StudyHelper.git
cd StudyHelper
npm install
npm run dev
```

Then open [http://localhost:3000](http://localhost:3000).

### API key

StudyHelper uses a **bring-your-own-key** model: you provide your own [Anthropic API key](https://console.anthropic.com/) in the app. The key is kept in your browser and used only to make your requests; it is not stored on a server. Usage is billed to your own Anthropic account.

## Roadmap

- [x] Project setup (Next.js, TypeScript, Tailwind, dependencies)
- [ ] Output schemas (concepts, summary, quiz)
- [ ] `/api/analyze` route with Claude PDF input
- [ ] Upload screen (drag & drop, API key, options)
- [ ] Results dashboard (concepts, summary, quiz player, flashcards)
- [ ] Local library of past study sets
- [ ] Deployment and demo

## Disclaimer

Quizzes and summaries are AI-generated and may contain mistakes. Always check them against your original course material.
