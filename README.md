# scoop-bucket

[Scoop](https://scoop.sh) bucket for [mctwain](https://github.com/mormitech/mctwain), a local helper that lets web
pages scan documents from network scanners. It also installs a tray icon that shows the scanners it found.

```
scoop bucket add mormitech https://github.com/mormitech/scoop-bucket
scoop install mctwain
```

mctwain starts right away and at every login (Scoop registers a startup entry for it). `scoop uninstall mctwain` stops
it and removes the startup entry.

The manifest `bucket/mctwain.json` is generated from a mctwain release by `scripts/make-scoop-manifest.mjs` in the
mctwain repository.

## Updating for a new mctwain release

```
node ../mctwain/scripts/make-scoop-manifest.mjs > bucket/mctwain.json
```

then commit and push. The `test` workflow installs the manifest with real Scoop on Windows and checks that mctwain
answers and uninstalls cleanly.
