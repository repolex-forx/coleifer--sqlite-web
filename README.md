# Repolex Knowledge Graph of coleifer/sqlite-web

RDF knowledge graph data for [coleifer/sqlite-web](https://github.com/coleifer/sqlite-web), parsed by [repolex](https://repolex.ai).

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
rlex download coleifer/sqlite-web
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 974a910019a31078df69fbe98901fe859d3089a3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 974a910019a31078df69fbe98901fe859d3089a3
│           └── chunk-001.nq.gz
├── blob
│   ├── 07e1bdfe328f711ab0de75ae2a289ee7ba56b630.nq.gz
│   ├── 0a319dfcbdd0a41eca7b50b2a61715fd37c7e459.nq.gz
│   ├── 2d347ccd1cf2f14d71764064345c265237c62b37.nq.gz
│   ├── 304a2e144a0566c11ebbf1f87ea64bbc6b01d839.nq.gz
│   ├── 330d5cfa2ed1b4ee7978d5a56c8ac89b358aa179.nq.gz
│   ├── 3353af2529ef8e769da26a1b312686aca953b8d0.nq.gz
│   ├── 386064a3ab0bedccc896de415789d294cf5887c2.nq.gz
│   ├── 399ba41334991c2f4bb0655dabfc4900b5fdd0d1.nq.gz
│   ├── 43a1617c799ad08f03edafc5dc3c859592082b1a.nq.gz
│   ├── 477d34f25b5638576bd88b4b8c2e015aab2796f1.nq.gz
│   ├── 4cb22ed17441daf4e06efceb4ffe893cee5ffd33.nq.gz
│   ├── 572698014c4b2ce1d776fdee52614ff370a4e09b.nq.gz
│   ├── 6fd07e2174bfd265039bc25ed6ebaad393e02d07.nq.gz
│   ├── 7444ba3e0cf04eb4ecb28cea6df39a4a5618de94.nq.gz
│   ├── 83b754a1eb1d51062f77b1aecde31e2c258d5cde.nq.gz
│   ├── 8635a5cbf6cfe4a6fc163571ce735b8f677a1efb.nq.gz
│   ├── 8cae04098219358c32eb591378498893bb46a833.nq.gz
│   ├── 9d66e8573cfc81d83b3cb3c32d8d0fb5ab4b0624.nq.gz
│   ├── 9fc352667ab388cc7c2c66a5502f5732c4b71b5f.nq.gz
│   ├── a3d46faacbaedaa3170680ab609bff741284c9ce.nq.gz
│   ├── aa78ab079bd64bb997b935d59e318e1008a1c809.nq.gz
│   ├── b94c4b32158436a45df39f4da64b7f3fe37e804e.nq.gz
│   ├── bb41720278b0fa8135d063e979a4ddfe1950446e.nq.gz
│   ├── c752ab3ead2e7be324e5cafb5e1d53135c16af13.nq.gz
│   ├── cf19b8ef25713ebfaff3325e4dcd9b8c260753c6.nq.gz
│   ├── d8d96d5e9d6ce5f2b649176c426d0db39bd7b37a.nq.gz
│   ├── d8e4df2c2b7a829ad0b35e5e1cfd95507658c358.nq.gz
│   ├── dadfdbdcd86a9f3e55e8fe2abfde1562da007f9c.nq.gz
│   ├── de6d264a416e7922c77456b3dfccdbd98011606d.nq.gz
│   ├── e1a27389b1bb07cdeb629c57c0a4341c439b9383.nq.gz
│   ├── e55d944ad7717e658ad5ff6ea18cd21cbf22ca14.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f200eca682e50e79431c332d17e59b34c129dd20.nq.gz
│   ├── f2b462b6aeb419c441e9f3d0c862328c1e392fd7.nq.gz
│   ├── f7d70ea706531fe6fbea028a88cd72f236e12f2c.nq.gz
│   └── ff42107d4c1e4b345d1f6042871094db0025fd78.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 974a910019a31078df69fbe98901fe859d3089a3.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[coleifer/sqlite-web](https://github.com/coleifer/sqlite-web)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
