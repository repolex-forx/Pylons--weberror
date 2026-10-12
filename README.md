# Repolex Knowledge Graph of Pylons/weberror

RDF knowledge graph data for [Pylons/weberror](https://github.com/Pylons/weberror), parsed by [repolex](https://repolex.ai).

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
rlex download Pylons/weberror
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8963e48ca7b1f803039b8dba1dea687dcefb0950
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 8963e48ca7b1f803039b8dba1dea687dcefb0950
│           └── chunk-001.nq.gz
├── blob
│   ├── 00cfbde500888e457f0f37806bdcf5c2c8b691d4.nq.gz
│   ├── 013998515cd7bf5d3f00af42178aa14015cd2aa5.nq.gz
│   ├── 05f330651a74a00113e231891b30f74b9cdcdf01.nq.gz
│   ├── 09d75480e3be3446502284cce8dc0b6afd642333.nq.gz
│   ├── 0c284570f61a862d24e7a834210e66e42985d767.nq.gz
│   ├── 11ab52365016d50ffc76951b88e8c29498b2ccce.nq.gz
│   ├── 17dabde8b08f08e81e51ea4a2f8907514c7d79a5.nq.gz
│   ├── 3cab8e2b2a4de804072d1664be11c4c7e92242a0.nq.gz
│   ├── 5b5e0c07bde858d842fd1bc1608441a8172b7ab3.nq.gz
│   ├── 5ce311dc35a7e3b4a6d4669f8735832af0c4bbe2.nq.gz
│   ├── 6e8c2cfcc9f58bef4878a04b9fe2665e6fab9f43.nq.gz
│   ├── 792d6005489ebee62cde02066f19c5521e620451.nq.gz
│   ├── 7ce0b6ae89070a1489d99c673673901d9bd062ea.nq.gz
│   ├── 7ee12bec519153ff46349c45a8b4c38299417381.nq.gz
│   ├── 7f94e5f30684b1cffedefd38dc820280b9dd7413.nq.gz
│   ├── 868a82d9e934023f691c3f9b8e294abe261310e5.nq.gz
│   ├── 94a1dbdadf9bd95e6f48b598ab4683b64b942f99.nq.gz
│   ├── 98ffcaba6c070ad51d761b78f5a34dd76f64ed72.nq.gz
│   ├── a17aa5eb5fd2326a8e1ad1537978e2b177eef161.nq.gz
│   ├── b15e3305e2160fed8248dd3e3259c3c02342f2a7.nq.gz
│   ├── b2e95ab504b581e1bff8f8138c21108284f0a276.nq.gz
│   ├── b9d696e754fb7ea61b042669ec5a8400627d8add.nq.gz
│   ├── bbf33bba4eda7dffe198592cf29f0d8206ee7e07.nq.gz
│   ├── c358f5962215615dd33b9920cbcb0705310dd858.nq.gz
│   ├── c4b9f7e9d92665a55cf1be9856b1f8cf519e898a.nq.gz
│   ├── c5e57f09e71e1fcf127101ad2a7e932a0f30e66f.nq.gz
│   ├── c64df38e2f6c70463c1adb9b79a0244a09087891.nq.gz
│   ├── c8dfeabfe16fbae7150dd43cf1fd8c1ee5c8f1d6.nq.gz
│   ├── d663fec167fa4e9ec6ef8880b30bbbe24fdc0832.nq.gz
│   ├── dd26be8c8c131653d4282cbb3527b63257f84dd8.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── eaa0b107cd4e3e3848ba93e0ad7f48b9d12fd7a3.nq.gz
│   ├── ead263de3082e2787c03be6d0d06b1b44ce90b87.nq.gz
│   ├── f042d0943086bb1195a2095dff75014aed683737.nq.gz
│   ├── f9085da86b5ac7ce6d4b97c22f6b33904e9889bd.nq.gz
│   └── f9261d6cf3496b3c48186f332000f42679e5c280.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8963e48ca7b1f803039b8dba1dea687dcefb0950.nq.gz
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

[Pylons/weberror](https://github.com/Pylons/weberror)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
