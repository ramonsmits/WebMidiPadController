# WebMidiPadController

Web MIDI pad controller — single-file app (`index.html`) served via GitHub Pages.

## Branches

- `main` — development branch, all commits go here
- `gh-pages` — serves GitHub Pages, must be kept in sync with `main`

After pushing to `main`, always fast-forward `gh-pages`:

```sh
git checkout gh-pages && git merge main --no-edit && git push && git checkout main
```

## Structure

Single file: `index.html` — contains all HTML, CSS, and JS inline. No build step.

## Key Architecture

- **Device panel**: collapsible panel with toggle switches for all MIDI inputs/outputs
- **Multi-output**: `enabledOutputs` Map — sends to all enabled outputs simultaneously
- **Input listening**: `enabledInputs` Map — receives feedback from toggled inputs
- **Persistence**: device preferences saved by **name** (not ID) in localStorage (`STORAGE_ENABLED_OUTPUTS`, `STORAGE_ENABLED_INPUTS`), since MIDI port IDs are ephemeral
- **Auto-reconnect**: `onstatechange` re-enables devices whose name matches saved preferences
- **Pad layout**: stored in localStorage (`STORAGE_KEY`), editable via JSON editor overlay

## Copy to sopund root

A copy of `index.html` also lives at `/home/ramon/Music/sopund/index.html`. Update it after changes:

```sh
cp index.html ../index.html
```
