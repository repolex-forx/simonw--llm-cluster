# Repolex Knowledge Graph of simonw/llm-cluster

RDF knowledge graph data for [simonw/llm-cluster](https://github.com/simonw/llm-cluster), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/llm-cluster
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d2f93f1d17abd001454cecd8de21c75138053d7b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d2f93f1d17abd001454cecd8de21c75138053d7b
│           └── chunk-001.nq.gz
├── blob
│   ├── 242e6cfa548d3a9aa4dc1adce6909d3e8d0655cf.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2932b81f03b4361168e8e1a6afb12230cd207ce8.nq.gz
│   ├── 6aa2decfe1bc3224261f53c8a3bc361db23ace5d.nq.gz
│   ├── 732e0d00e00846b8e760898eaaad5db46fc0b62f.nq.gz
│   ├── 810e36cde22a33de5f34d80458c5b8e21bf1a3da.nq.gz
│   ├── 8bfc65af963ec7121bc2ca784716868f6a5188d6.nq.gz
│   ├── 9dc8b3f922ea98f39300f30791c492283a233f0f.nq.gz
│   └── e61ce1d68a38f43ce1ad952ccdb94f9ab7d69670.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d2f93f1d17abd001454cecd8de21c75138053d7b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[simonw/llm-cluster](https://github.com/simonw/llm-cluster)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
