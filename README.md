# Amazon Lite - pxml specification

This is an Amazon-like online store built entirely using structured XML specifications and compiled using the `pxml` compiler.

## Features
- **Scaffolding Setup**: Automates Next.js initialization with Tailwind CSS.
- **Product Catalog (`flows/catalog.xml`)**: SQLite seeding database of 10+ products across multiple categories. Grid view, search, and catalog filtering.
- **Shopping Cart (`flows/cart.xml`)**: Amazon-styled cart page supporting quantity changes, item removal, and database syncing.
- **Checkout & Orders (`flows/checkout.xml`)**: Address forms, placing order APIs, clearing active carts, and order history receipts.

## How to Compile and Run

### 1. Build & Compile with AI
Run the compiler inside this directory with your chosen AI provider (for example, using OpenAI):
```bash
export OPENAI_API_KEY="your-api-key"
pxml compile --provider openai --model gpt-4o
```
This will automatically execute the setup commands, install the required packages (`better-sqlite3`), and write all component codes.

### 2. Run Next.js Local Server
Once compilation finishes successfully:
```bash
npm run dev
```
Open `http://localhost:3000` to browse your Amazon Lite store!

### 3. Check Manifest State
All compiler build records, generated files, hashes, and lock parameters are tracked in `.pxml/manifest.json`.
