# vibe-index — `vibespecs`

Metadata index for the vibevm registry `vibespecs` (`https://github.com/vibespecs`).
Format: [PROP-005](https://gitverse.ru/vibevm/vibevm/raw/branch/main/spec/modules/vibe-index/PROP-005-package-index.md).

## Files

- `hello.json` — the eternal handshake: the client's entry point,
naming the worlds that exist and where each lives.
- `repomd.json` — manifest with sha256 of every catalog file the
writer produces. `hello.json` is deliberately outside it: this
manifest describes ONE world, the handshake stands above worlds.
- `primary.jsonl` / `primary.jsonl.gz` — one `VersionEntry` per line.
- `by-name/<name>.json` — candidate set for one bare name (every group).
- `by-cap/<slug>.jsonl` — inverted index by advertised capability.
- `by-purl/<slug>.jsonl` — inverted index by `describes` PURL.
- `state/` — gitignored runtime data, never published: the fact
JOURNAL this catalog is projected from, plus the server PID,
admin tokens and the incremental-reindex checkpoint. Back up
`state/journal/`; everything above it is derived.

## Maintenance

Refresh from the authoritative org clones with:

```sh
vibe-index reindex . --from-clones <org-dir> --incremental
```

Or walk a GitHub org directly:

```sh
vibe-index reindex . --from-github <org> --token-file <pat-file>
```

See `crates/vibe-index/docs/` in the vibevm source tree for
the full operator handbook + consumer protocol + format reference.
