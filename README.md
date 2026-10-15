# VS Code Dark Modern for Tern

A [Tern](https://stencil.so/tern) plugin that paints Tern with VS Code's
**Dark Modern** theme: window chrome, terminal grid and ANSI palette, the file
editor's syntax colors, and the editor's own line numbers, guides, cursor,
selection, find matches and git gutter.

Tern 0.8 or later. Only the dark appearance is styled; the light appearance
stays Tern's.

## Install

    tern plugin install github.com/ITSyndicate25/tern-vscode-dark

Or from a clone, where it runs in place:

    git clone https://github.com/ITSyndicate25/tern-vscode-dark.git
    tern plugin link tern-vscode-dark

Check it loaded:

    tern plugin list
    # vscode-dark 1.0.0 VS Code Dark Modern — 0 blocks, 0 lenses, window  ready

Remove it with `tern plugin remove vscode-dark`, or `tern plugin unlink
vscode-dark` after a link. A window that was already open when the plugin
appeared picks it up after `tern plugin reload` or a restart; new windows get
it at once.

## What it sets

| Area | Variables |
| --- | --- |
| Chrome | page and popover material, cards, raised controls, code blocks, text steps, accent, status colors |
| Terminal | background, foreground, cursor, selection, ANSI 0–15 |
| Syntax | `--tk-*`, the file editor's token colors |
| Editor | `--ed-num`, `--ed-num-cur`, `--ed-caret`, `--ed-guide`, `--ed-bracket`, `--ed-link`, `--ed-thumb`, `--ed-diag-error`, `--ed-diag-info`, `--ed-git-mod`, `--ed-mark`, `--ed-hit` |

Every value carries the VS Code key it came from in `vscode.css`, so a color
can be traced back to `dark_modern.json`, the `dark_plus.json` and
`dark_vs.json` it includes, or the color-registry default in VS Code's
workbench bundle. Nothing else is styled: Tern derives its own surfaces,
radii, motion and light appearance.

## Notes

- **Liquid Glass.** The sheet sets the theme's page and popover colors, not
  the values Tern derives from them, so a glass window keeps its translucency
  and its opacity setting. Measured in a window on Liquid Glass, the panel
  composites to about `#1d1d1d` instead of `#1f1f1f`; the exact value depends
  on the material, its opacity and the backdrop, so use a solid material when
  you want `#1f1f1f` on screen.
- **One keyword color.** Tern's highlighter has a single keyword token, so
  `if`, `return` and `foreach` render `#569cd6` like `public` and `static`,
  instead of VS Code's `#c586c0` for control flow.
- **Current line.** Tern fills the current line with `--ed-line`; Dark Modern
  sets `editor.lineHighlightBackground` to `null` and draws only a `#282828`
  outline, so the sheet leaves `--ed-line` at Tern's faint fill rather than
  painting that border color as a band.

## License

MIT.
