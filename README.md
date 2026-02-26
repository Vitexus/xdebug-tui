Debug-TUI
=========

Interactive [Xdebug](https://xdebug.org) step-debugging client for your terminal.

![Demo](https://github.com/user-attachments/assets/1a8a1d1b-d01b-4d71-9d35-c65e546e8c24)

- **Travel forwards**: step over, into and out.
- **Travel backwards**: it's not quite time travel - but you can revisit
  and inspect previous steps in _history mode_.
- **Jump the stack**: jump up and down the stack.
- **Vim-like motions**: Typing `100n` will repeat "step into" 100 times.
- **Inline values**: Show variable values inline with the source code.
- **Process control**: Launch, monitor and restart the process being debugged.

## Installation

- Download the [latest release](https://github.com/dantleech/debug-tui/releases/latest).
- Compile it yourself `cargo build`.
- Install the Debian package: `sudo dpkg -i xdebug-tui_*.deb`

### Building the Debian package

```bash
dpkg-buildpackage -us -uc -b
```

## CLI options

- `--log`: Debug log to file.
- `--listen`: Listen on an alternative address (defaults to `0.0.0.0:9003`).

In addition you can optionally specify a process to debug:

```bash
$ debug-tui -- php path/to/script.php
```

## Key bindings

Prefix with number to repeat:

- `r`     run
- `n`     next / step into
- `N`     step over
- `p`     previous (switches to history mode if in current mode)
- `o`     step out
- `R`     restart process if one was provided
- `j`     down
- `J`     down 10
- `k`     up
- `K`     up 10
- `h`     left
- `H`     left 10
- `l`     right
- `L`     right 10
- `+`     increase context depth
- `-`     decrease context depth
- `tab`   switch pane
- `enter` toggle pane focus (full screen)
- `t`     rotate the theme
- `?`     Show help
- `f`     Filter (context pane) - use dot notation to filter on multiple levels.

## Setting Breakpoints

`debug-tui` has no mechanism for setting a breakpoint but you can use the
function `xdebug_break()` in your code:

```php
<?php

function my_function() {
    xdebug_break(); // break after this line
}
```
