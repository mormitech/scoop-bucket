# scoop-bucket

[Scoop](https://scoop.sh) bucket for [mormiDiskFree](https://github.com/mormitech/mormidiskfree), a disk space analyzer, for [mormiPrint](https://github.com/mormitech/mormiprint), a free scanning app, for [mormiView](https://github.com/mormitech/mormiview), a picture viewer with a small editor, and for [mctwain](https://github.com/mormitech/mctwain), a local helper that lets web
pages scan documents from network scanners. It also installs a tray icon that shows the scanners it found.

```
scoop bucket add mormitech https://github.com/mormitech/scoop-bucket
scoop install mormidiskfree # the disk space analyzer
scoop install mormiprint # the scanning app
scoop install mormiview # the picture viewer and editor
scoop install mctwain   # the local helper
```

mctwain starts right away and at every login (Scoop registers a startup entry for it). `scoop uninstall mctwain` stops
it and removes the startup entry.

The manifest `bucket/mctwain.json` is generated from a mctwain release by `scripts/make-scoop-manifest.mjs` in the
mctwain repository.

## Updating for a new release

mormidiskfree: `node ../mormidiskfree/scripts/make-scoop-manifest.mjs > bucket/mormidiskfree.json`.

mormiprint: `node ../mormiprint/scripts/make-scoop-manifest.mjs > bucket/mormiprint.json`.

mormiview: `node ../mormiview/scripts/make-scoop-manifest.mjs > bucket/mormiview.json`.

mctwain:

```
node ../mctwain/scripts/make-scoop-manifest.mjs > bucket/mctwain.json
```

then commit and push. The `test` workflow installs the manifest with real Scoop on Windows and checks that mctwain
answers and uninstalls cleanly.
