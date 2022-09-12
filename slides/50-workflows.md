<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## C++ Workflows in neovim

Note:
- Now on to the live demos where we get to play Donkey.
- I'll switch over to my Terminal, where everytime I fail terribly, I earn
  a letter.
- Lets see if I can avoid making an ass of myself.
  - So I have 5 lives basically.
- I'll also start a program which shows what keys I'm pressing on the top right
  corner, so that you can follow along.
- I'll also mention my mnemonics as I use my keybindings.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Open File, No LSP

Live demo

Note:
- Move to Neovim pane
- Zoom tmux
- Mention `z` in Window name.
- Open `netrw`
- Open Telescope
  - `<Leader>fp`
  - `fp` = Project files
  - Its reverse becase all my telescope mappings start from `f`
- Type `cpp`
- Delete `cpp`, type `main`
- Open `app_main.cpp`
- Zoom out a bit to show preview, then zoom back in
- Next slide - LspInfo not working 

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### `:LspInfo` - Not attached

Live demo

Note:
- No Lsp attached
- `<Leader>fzv` - fuzzy find `clangd.lua`, show `compile_commands.json` root
  configuration for clangd.
- I don't want to see errors unnecessarily.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Tree-sitter highlighting

Live demo

Note:
- Enable/disable highlight
  `:TSBufToggle highlight`
- Different kinds of identifiers are highlighted using different colours,
  because treesitter is doing the highlighting based on the abstract syntax
  tree.
- Use treesitter `vif` inside `add_number_options()` to select everthing in the
  function.
- Mention that it works without Lsp
- Treesitter can do a lot more, and there are plugins which use it provide
  additional features.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Project navigation

Live demo

Note:
- Switch over to the `configured` branch
- Open Neovim
- Open `netrw`
- Open Telescope
- Type `cpp`
- Delete `cpp`, type `main`
- Open `app_main.cpp`
- Zoom out a bit to show preview, then zoom back in
- Show `clangd` status on the bottom right corner
- Close Neovim, `rm -rf ./.cache`
- Open Neovim vim, use telecope to open `app_main.cpp`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### `:LspInfo`

Live demo

Note:
- Show LspInfo
- Mention clangd attaches to the buffer

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Buffer, File, Window and Tabs

Live demo

Note:
- Split
- Horizontal split
- `gt` and `gT`
- Goto tab
- In Vim, in general capital letters go in the reverse direction of their
  lowercase counterparts.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Intellisense - Add multiply

Live demo

Note:
- Implement multiply in 2 ways
- First without LSP using regular vim
  - Use `:LspStop` to stop lsp
  - Copy `sub` `add_subcommand`
- With lsp
  - Delete the line, typing everything out manually.
  - Mention live error
  - Show intellisence working
- There are plenty of ways to do the same things in Neovim...

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Clang format

Live demo

Note:
- `<Leader>gf` = Go format
- Make `app.add_subcommand("mul", "Multi...")` break at `.` and `,` and auto-format.
- I also have a `.clang-format` file in the root of the repo.
- `clangd` already has an integration with `clang-format` and I can format the
  buffer by pressing my keybinding for it.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Navigate between diagnostics

Live demo

Note:
- `]d` and `[d` to move between diagnostics
  - `d` for diagnostics
- Diagnostics is a general term which refers to errors, warnings as well as
  hints.
- One of the hints you're seeing is actually coming from `clang-tidy` because
  `clangd` already has that integrated into it.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Clang-tidy integration

Live demo

Note:
- Show hints

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Trouble integration

Live demo

Note:
- Modern alternative for quickfix/location list, which are really hard to
  navigate around.
  - Everyone uses legendary Vim plugin author Tim Pope's unimpaired plugin to
    navigate quickfix lists.
- We don't have to get into what those are.
- `<Leader>xd` - `x` for error, `d` for document
- `<Leader>xs` - `x` for error, one more `x` for in project.
- Built-in keybindinds which make sense to me.
- Show what trouble does based on the previous slide

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Code actions

Live demo

Note:
- `<Leader>ca`
- LSP suggests code actions.
- We're halfway through the demo.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Go to definition/declaration

Live demo

Note:
- `<Leader>gd` - Go to definition
- `<Leader>gD` - Go to declaration
- `<Leader>gt` - Go to type declaration

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Switch between header/cpp

Live demo

Note:
- `<Leader>gs` - Go switch

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Find references

Live demo

Note:
- Open adder
- `<leader>rf` - references

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Refactor

Live demo

Note:
- `<Leader>rn` - Rename
- Rename `m_numbers`
- Show trouble window again
- `:wall`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Document symbols

Live demo

Note:
- Open adder
- `<leader>lds`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Run executable

Live demo

Note:
- TBD

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Debugging

- [Debug Adapter Protocol][dap]
- [nvim-dap][nvim-dap]

[dap]: https://microsoft.github.io/debug-adapter-protocol/
[nvim-dap]: https://github.com/mfussenegger/nvim-dap

Note:
- One this you may have noticed I didn't cover is visual debugging.
- This is primarily because I use gdb whenever I need to debug a task.
- But like LSP, there is something called the Debug Adapter Protocol and there
  is a plugin called `nvim-dap` which can provide visual debugging.
  - I haven't tried it out, so I'm not going to be covering it here.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Multi-language setup

Live demo

Note:
- Show `tasks.py`, show `:LspInfo`
- Show `<leader>lds` for symbols in the current project
- Show `do_config()`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Multi-language setup

The same setup works whether you're working on Rust, Golang,
JavaScript/TypeScript, Zig, etc...

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- ~Context~
- ~Command Line Environment~
- ~C++ Workflows with Neovim~
- Neovim Setup <!-- .element: class="fragment grow highlight-green" -->

Note:
# Pause for questions
