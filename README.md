# Repolex Knowledge Graph of glue-viz/glue-qt-ai

RDF knowledge graph data for [glue-viz/glue-qt-ai](https://github.com/glue-viz/glue-qt-ai), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download glue-viz/glue-qt-ai
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 90c3ae2ca7d3617c6ffbc52eec694e65eaa84f99
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 90c3ae2ca7d3617c6ffbc52eec694e65eaa84f99
│           └── chunk-001.nq.gz
├── blob
│   ├── 3692b8ee9425eddea03b68bf1f6d8ccebe4f70c1.nq.gz
│   ├── 6ba22f4cb3b724c36887e9f9ac2fe101a8c2bd76.nq.gz
│   ├── 86ea2138e29dd3523a552924851126cf2e6203e9.nq.gz
│   ├── 98ac78a581af3901fd396ef74ef77dd36537182c.nq.gz
│   ├── c5e0f3cef274b45b04d8c9bc7f701f8d20a08f6a.nq.gz
│   └── f5efe2746e10df728c50f03288bf6999bac09f24.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 90c3ae2ca7d3617c6ffbc52eec694e65eaa84f99.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 12 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[glue-viz/glue-qt-ai](https://github.com/glue-viz/glue-qt-ai)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
