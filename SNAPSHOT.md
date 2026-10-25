# The one thing that exists: the Pydantic docs snapshot

Made 2026-10-24 on my machine. It isn't committed here: the full clone is about 6 MB and is someone else's MIT-licensed repository.

| Field | Value |
|---|---|
| Source | https://github.com/pydantic/pydantic |
| Tag | v2.14.1 (HISTORY.md: "v2.14.1 (2026-10-11)") |
| Commit | `b2212c787fb5c73386dc770681ec49cd09da8e73` |
| Docs pages | 91 Markdown files under `docs/` |
| Words | 82,272 (`find docs -name "*.md" -print0 \| xargs -0 cat \| wc -w`) |
| Licence | MIT (the repository's `LICENSE`) |

Reproduce:

```bash
git clone --depth 1 --filter=blob:none --branch v2.14.1 https://github.com/pydantic/pydantic pydantic-v2.14.1
cd pydantic-v2.14.1 && git rev-parse HEAD          # expect b2212c78…
find docs -name "*.md" | wc -l                       # expect 91
```

Nothing has been indexed, chunked or queried yet.
