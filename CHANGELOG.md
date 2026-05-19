## [1.0.2](https://github.com/marslo/batchip/compare/v1.0.1...v1.0.2) (2026-05-19)

### Code Refactoring

* refactor(rename): rename to batchip ( from batcolor )
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Documentation

* docs: update readme
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Bug Fixes

* fix(core): fixed the double ANSI escape rendering in pipe mode

Fixed #3
Signed-off-by: marslo <marslo.jiao@gmail.com>
* fix(core): optimize pipe mode to bypass bat and its env vars
  - color filter directly WITHOUT `bat` when stdin is piped and no args given - `cat file | batchip`
  - skip BAT_OPTS/BAT_STYLE env manipulation in pipe mode, since the options might be provided by bat previously - `bat -p --color always file | batchip`
  - add github actions pre-commit workflow

Fixed #1

Signed-off-by: marslo <marslo.jiao@gmail.com>

## [1.0.1](https://github.com/marslo/batcolor/compare/v1.0.0...v1.0.1) (2026-05-17)

### Documentation

* docs: update README.md and add screenshots
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Others

* chore: introduce pre-commit hook
  Signed-off-by: marslo <marslo.jiao@gmail.com>

### Bug Fixes

* fix(core): resolve pipe rendering and preserve native bat highlights
  - suppress phantom line numbers during pipe input (! -t 0) by stripping global BAT_OPTS and enforcing `BAT_STYLE=plain` via `env` command
  - refactor `_color_filter` Perl regex to safely inject background ANSI codes without stripping bat's native foreground syntax highlighting
  - restore Rec. 709 luma algorithm to dynamically set text to black or white for readability inside color blocks
  - prevent color bleed into subsequent text by replacing the hardcoded trailing color with a standard reset (`\033[39;49m`)

Fixed #1

Signed-off-by: marslo <marslo.jiao@gmail.com>

## 1.0.0 (2026-05-16)

### Features

* feat(init): init the batcolor
  Signed-off-by: marslo <marslo.jiao@gmail.com>
