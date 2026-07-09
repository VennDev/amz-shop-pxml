# Amazon Lite — pxml Project

An Amazon-like online store built entirely with **structured XML specs** and
compiled by the **pxml** compiler. Uses the `ui-ux-components-pxml` library
for UI pages (login, product grid, cart, checkout, order history) extended
with custom Amazon-dark style constraints.

## Features

- **Catalog (`flows/catalog.xml`)** — 10+ products seeded in SQLite, grid view,
  product cards with images/prices, add-to-cart via `/api/cart`.
- **Shopping Cart (`flows/cart.xml`)** — quantity stepper, remove item, syncs
  with backend DB.
- **Checkout & Orders (`flows/checkout.xml`)** — shipping form → place order →
  order history receipt.
- **Auth (`flows/auth.xml`)** — login/register with session cookies.
- **UI Components** extend from `ui-ux-components-pxml` (login, productGrid,
  cart, checkout, orderHistory) — each with an attached `llm-judge` prompt
  for Amazon-style theming.

## Quick Start

### 1. Install pxml

```bash
npm install -g @two-tech-dev/pxml
```

### 2. Install packages

```bash
pxml install
```
This reads `pxml.json` and clones `ui-ux-components-pxml` into
`packages/ui-ux-components-pxml/` (plus binds its editor schema).

### 3. Validate

```bash
pxml validate
```
Generates an alias-aware enriched schema → your editor suggests exact
`extends="uix:auth:login"`, `flow="auth"`, etc. automatically.

### 4. Compile with AI

```bash
export OPENAI_API_KEY="your-api-key"   # or ANTHROPIC_API_KEY
pxml compile --provider openai --model gpt-4o
```

### 5. Run

```bash
npm run dev
```

## How It Works

- `project.xml` — imports flows + UI library, defines setup/config/db nodes.
- `flows/*.xml` — API routes and UI page specs (extend `ui-ux-components-pxml`).
- `packages/ui-ux-components-pxml/` — installed by `pxml install` (gitignored).
- `pxml.json` — manifest tracking the pxml version and package dependencies.

### Editor Autocomplete

`pxml validate` auto-generates an enriched schema that enumerates all valid
`flow` values, node `type`s, and exact `extends` values (`uix:auth:login`,
`uix:ecommerce:productGrid`…). VS Code (Red Hat XML extension) picks it up
via `.pxml/catalog.xml` — zero config.

## Preview

![Amazon Lite](https://github.com/user-attachments/assets/12ff88f1-856c-497e-8fa9-10b51f045864)
