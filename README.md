# Neovim config

A small, standalone Neovim config using [lazy.nvim](https://github.com/folke/lazy.nvim). It needs Neovim 0.11 or newer for the native `vim.lsp.config` API.

```
init.lua                  loads options, then keybinds, then lazy
lua/config/options.lua    editor settings
lua/config/keybinds.lua   general keymaps
lua/config/lazy.lua       lazy.nvim bootstrap (loads lua/plugins/*)
lua/plugins/*.lua         one plugin spec per file
```

## Recent keymap changes

| Old | New | Action |
|---|---|---|
| `<leader>dg` | `<leader>gd` | Generate a docblock (vim-doge). Moved so `<leader>d` runs without waiting. |
| `<leader>fg` (git files, shadowed) | `<leader>fG` | Telescope git files. `<leader>fg` stays the grep prompt. |

## Keymaps

Leader is `<Space>`.

### Editing and navigation

| Mode | Key | Action |
|---|---|---|
| n | `<leader>cd` | Open the file explorer (netrw) |
| v | `J` / `K` | Move the selection down / up |
| n | `J` | Join lines, keeping the cursor in place |
| n | `<C-d>` / `<C-u>` | Half-page down / up, centred |
| n | `n` / `N` | Next / previous search match, centred |
| x | `<leader>p` | Paste over the selection without copying the replaced text |
| n, v | `<leader>d` | Delete without copying |
| i | `<C-c>` | Escape |
| n | `<C-k>` / `<C-j>` | Next / previous quickfix item |
| n | `<leader>k` / `<leader>j` | Next / previous location-list item |
| n | `Q` | Disabled (no Ex mode) |
| n | `<leader>s` | Substitute the word under the cursor on the current line |
| n | `<leader>x` | Make the current file executable |
| n, v | `<leader>y` | Copy to the system clipboard over SSH (OSC 52) |
| n | `<leader>u` | Toggle undotree |
| n | `<leader>gd` | Generate a docblock (vim-doge) |
| n | `<leader>cc` | Run `php-cs-fixer` on the current file |
| n | `<leader>rl` | Reload `init.lua` |
| n | `<leader><leader>` | Source the current file |

### Telescope

| Key | Action |
|---|---|
| `<leader>ff` | Find files |
| `<leader>fG` | Git files |
| `<leader>fg` | Grep for a string you're prompted for |
| `<leader>fs` | Grep the string under the cursor |
| `<leader>fc` | Grep the current file's name (to find where it's included) |
| `<leader>fo` | Recently opened files |
| `<leader>fb` | Buffers |
| `<leader>fq` | Quickfix list |
| `<leader>fh` | Help tags |
| `<leader>fi` | Find files in this config |

Inside the picker (insert mode), `<C-j>` / `<C-k>` move through the results, and `<C-q>` sends the selected results to the quickfix list.

### Harpoon

| Key | Action |
|---|---|
| `<leader>a` | Add the current file |
| `<C-e>` | Toggle the quick menu |
| `<leader>fl` | Show the list in Telescope |
| `<C-p>` / `<C-n>` | Previous / next file |

### LSP (when a server is attached)

| Key | Action |
|---|---|
| `K` | Hover |
| `gd` / `gD` | Definition / declaration |
| `gi` | Implementation |
| `go` | Type definition |
| `gr` | References |
| `gs` | Signature help |
| `gl` | Line diagnostics |
| `<F2>` | Rename |
| `<F3>` | Format (normal and visual mode) |
| `<F4>` | Code action |

Lua files are formatted on save.

### Completion (insert mode)

| Key | Action |
|---|---|
| `<Tab>` / `<S-Tab>` | Next / previous item (`<Tab>` also opens the menu) |
| `<CR>` | Confirm the selected item |
| `<C-e>` | Open / close the menu |
| `<C-f>` / `<C-u>` | Scroll the documentation down / up |
| `<C-d>` / `<C-b>` | Jump to the next / previous snippet placeholder |

## Language servers

Mason installs these, and they start automatically: `lua_ls`, `intelephense`, `ts_ls`, `eslint` and `clangd`. `stylua` is excluded from starting as a server.
