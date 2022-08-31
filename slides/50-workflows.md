<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## C++ Workflows in neovim

Note:
- Now on to the part where we get to play Donkey.
- I'll switch over to my Terminal for the live demos, where everytime I fail
  terribly, I earn a letter.
- Let me also start a program which shows what keys I'm pressing, so that you
  can follow along.
- I'll also mention my mnemonics as to what makes sense to me.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Project navigation

Live demo

Note:
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
### Tree-sitter highlighting

Live demo

Note:
- Enable/disable highlight
  `:TSBufToggle highlight`
- Use treesitter `vif` inside `add_number_options()` to select everthing in the
  function.
- Treesitter can do a lot more, and there are plugins which use it provide
  additional features.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### `:LspInfo`

Live demo

Note:
- Command mode
- This wouldn't be attached if I didn't have `compile_commands.json` file.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Buffer, File, Window and Tabs

Live demo

Note:
- Split
- Horizontal split
- `gt` and `gT`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Intellisense

Live demo

Note:
- Implement multiply
  - Copy `sub` `add_subcommand`
  - Mention live error
- Delete the line, typing everything out manually.
  - Show intellisence working
- Mention `nvim-cmp`
- Mention `lsp_signature`
- Mention `lightspeed`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Clang format

Live demo

Note:
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
- Diagnostics is a general terms which refers to errors, warnings as well as
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
- Modern alternative for quickfix/location list.
- We don't have to get into what those are.
- Show what trouble does based on the previous slide

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Code actions

Live demo

Note:
- TBD

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Go to definition/declaration

Live demo

Note:
- TBD

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Switch between header/cpp

Live demo

Note:
- TBD

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Find references

Live demo

Note:
- Open adder
- `<leader>rf`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Refactor

Live demo

Note:
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
