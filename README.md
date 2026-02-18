# treesitter-compiler

Shell (`zsh`) script for compiling and installing tree-sitter grammars compatible with installed version of **Emacs** on macOS.

This script is useful in cases where the built-in `tree-sitter` or equivalent vendor packages (`treesit-auto`, for example) cannot install language grammars due to version mismatch. In particular, this is the case when `tree-sitter` in Emacs gives `The installed language grammar for <LANGUAGE> cannot be located or has problems (version-mismatch): XX` warning and running `M-: (treesit-library-abi-version)` gives `YY`, confirming the version mismatch.

## Usage

The code and its usage is self-explanatory, but requires a basic understanding of Shell scripting. Ensure that `zsh`, a `C` compiler and `make` are available on your system. Language grammars are pulled from Github repositories if and when needed. In your `emacs.d/init.el`, prevent `treesit-auto` from overwriting language grammars with `(setq treesit-auto-install nil)`. For built-in `tree-sitter` avoid using `M-x treesit-install-language-grammar`.

``` shell
chmod +x ./treesitter-compiler && ./treesitter-compiler
```

### Language grammars

Edit the following in the script to add or remove grammars as needed. Note that the paths (urls) should point to the directory containing `parse.c` and `scanner.c`. 

``` shell
declare -A grammars=(
    ["python"]="https://github.com/tree-sitter/tree-sitter-python"
    ["javascript"]="https://github.com/tree-sitter/tree-sitter-javascript"
    ["jsdoc"]="https://github.com/tree-sitter/tree-sitter-jsdoc"
    ["html"]="https://github.com/tree-sitter/tree-sitter-html"
    ["css"]="https://github.com/tree-sitter/tree-sitter-css"
    ["json"]="https://github.com/tree-sitter/tree-sitter-json"
    ["bash"]="https://github.com/tree-sitter/tree-sitter-bash"
    ["php"]="https://github.com/tree-sitter/tree-sitter-php"
    ["elisp"]="https://github.com/Wilfred/tree-sitter-elisp"
    ["ruby"]="https://github.com/tree-sitter/tree-sitter-ruby"
    ["markdown"]="https://github.com/tree-sitter-grammars/tree-sitter-markdown"
    ["markdown-inline"]="https://github.com/tree-sitter-grammars/tree-sitter-markdown"
    ["zsh"]="https://github.com/tree-sitter-grammars/tree-sitter-zsh"
    ["scss"]="https://github.com/tree-sitter-grammars/tree-sitter-scss"
    ["csv"]="https://github.com/tree-sitter-grammars/tree-sitter-csv"
    ["toml"]="https://github.com/tree-sitter-grammars/tree-sitter-toml"
    ["make"]="https://github.com/tree-sitter-grammars/tree-sitter-make"
)
```
