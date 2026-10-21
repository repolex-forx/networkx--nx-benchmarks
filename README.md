# Repolex Knowledge Graph of networkx/nx-benchmarks

RDF knowledge graph data for [networkx/nx-benchmarks](https://github.com/networkx/nx-benchmarks), parsed by [repolex](https://repolex.ai).

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
rlex download networkx/nx-benchmarks
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 25dccf000484758ce070d13def9a3341843f0a1f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 25dccf000484758ce070d13def9a3341843f0a1f
│           └── chunk-001.nq.gz
├── blob
│   ├── 1d4c4afbeef6dd9dd33426c3851305b522682f21.nq.gz
│   ├── 29ee529e894a4bdb97b01ccf598f5f4195bf43ca.nq.gz
│   ├── 32e34050cafb1356d89d8c8280912aab0b4027d4.nq.gz
│   ├── 3b5feb23110adf02dcff9d28dda77d9193c06214.nq.gz
│   ├── 443a66829b6ee988a2990f8609e256d731dec3fe.nq.gz
│   ├── 4e75046943be1890052c28d64880f2d860b4a08c.nq.gz
│   ├── 68bc17f9ff2104a9d7b6777058bb4c343ca72609.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   └── d9682d4eb56f707b5a90f06efec15080236d4517.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 25dccf000484758ce070d13def9a3341843f0a1f.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 16 files
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

[networkx/nx-benchmarks](https://github.com/networkx/nx-benchmarks)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
