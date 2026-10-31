# Contributing

- Keep pages concise. Prefer tables, bullets and diagrams over prose.
- Diagrams are Mermaid fenced blocks (` ```mermaid `) so GitHub renders them.
- New problems copy [`_template.md`](04-problem-breakdowns/_template.md) and include exactly one high-level design diagram.
- New agentic problems copy [`05-agentic-problem-breakdowns/_template.md`](05-agentic-problem-breakdowns/_template.md). They include one high-level design diagram and may add one optional workflow or sequence diagram for the agent loop, plus the mandatory "Agentic Concerns" block.
- Core concepts and problems stay vendor-neutral. Vendor and Azure specifics belong in `03-key-technologies/`.
- Core concepts and key technologies live in numbered topic subfolders (for example `02-core-concepts/02-data/`). Add new pages to the closest group and link them from the README.
- Pages about fast-moving products (Foundry, MCP, agent frameworks) carry a `Last verified: YYYY-MM` line. Check claims against the official docs before updating it.
- Write original content. Do not paste text from books, courses or articles.
- State numbers as order-of-magnitude assumptions and say when they drive a design decision.
