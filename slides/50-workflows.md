<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## C++ Workflows with Neovim

Note:
- Now on to the live demos where we get to play Donkey.
- I'll switch over to my Terminal, where everytime I fail terribly, I earn
  a letter.
- Lets see if I can avoid making an ass of myself.
  - So I have 5 lives basically.
  - I don't get a letter if its not my fault.
  - And I'll decide whose fault it is.
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
  - All of my telescope files related keybindings start with an `f` for file
  - `<Leader>fp` - files in project
- This is an example of a Terminal User Interface, or Text User Interface
- Zoom out a bit to show preview, then zoom back in
- Type `cpp`
- Delete `cpp`, type `main`
- Open `app_main.cpp`
- **Pause**
  - Ask if everything is legible
  - Is the font size good
- And this is the file you were seeing in the screenshot earlier.
- A file loading into neovim is called a buffer. So you'll see me using the
  terms file and buffer interchangeably.
  - I'll talk more about that in just a bit.
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
- I mentioned earlier that a file loaded into Vim is called a buffer.
- But what you're seeing here is a window, and in Vim, a window is a view over
  that buffer.
  - Kind of like `std::span` is a view over a `std::vector`
- You can have multiple windows with a view over the same buffer.
- Split
- Horizontal split
- And then you can have tabs.
- Open `adder.cpp`
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
- Add a few more errors in the code and show that we get real time feedback on
  the errors.
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
- Lets created a few more trivial errors
- Neovim has a unified diagnostics api which makes the display or errors, warnings, hints unified.
- I'm configured moving between diagnostics to `]d` and `[d`
  - `d` for diagnostics
- Diagnostics is a general term which refers to errors, warnings as well as
  hints.
- One of the hints you're seeing is actually coming from `clang-tidy` because
  `clangd` already has that integrated into it.
- We'll revisit the fix available piece in just a bit. I have 1 more thing to
  show before that.

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
- We don't have to get into what those are, I'm just going to show the Trouble
  plugin.
- First of all, great job with the name "Trouble"
- I'm using trouble's suggested keybindinds
- `<Leader>xd` - `x` for error, `d` for document
- `<Leader>xx` - `x` for error, one more `x` for in project.
- Built-in keybindinds which make sense to me.
- Show what trouble does based on the previous slide

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Code actions

Live demo

Note:
- Now lets go ahead and fix those errors.
- LSP suggests code actions to us as well for trivial errors.
- `<Leader>ca`
- We're halfway through the demo.
- Let me see if can pause for questions.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Go to definition/declaration

Live demo

Note:
- Now lets see how we would explore the codebase.
- `<Leader>gd` - Go to definition
- `<Leader>gD` - Go to declaration
- `<Leader>gt` - Go to type declaration
- Ctrl+O and Ctrl+I
- Lets also get rid of the diagnostics here
- Fix nested namespace being contatenated
- Fix trailing return type
- Fix comment being incorrect because toddlermath namespace comment got deleted
- Show header-cpp switch to fix the remaining diagnostic
- I could bring up telescope and type `add.h` to go to that file. But clangd
  provides a non-lsp feature to switch between header and cpp.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Switch between header/cpp

Live demo

Note:
- `<Leader>gs` - Go switch
- Switch to header
- Typically what I do is I'll split the buffer into another window, and run
  `<Leader>gs` in that, so that I have both the header and cpp files opened at
  the same time.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Find references

Live demo

Note:
- Open adder
- I have this variable called `m_nums` here which is not the best name for this
  variable.
- I want to rename this.
- Before I did that I want to just see how many places its being referenced from
- `<leader>rf` - references

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Refactor

Live demo

Note:
- `<Leader>rn` - Rename
- Rename `m_nums` to `m_numbers`
- I get errors
- That is because neovim has updated the buffers where that variable was being
  referenced but the buffers haven't been saved yet.
- Show trouble window again
- `:wall` - write all

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
### Multi-language setup

Live demo

Note:
- Since I opened a lot of files, I'm going to just quit vim to get a fresh
  start for the next piece.
- One of the things I mentioned earlier was that the language server attached
  to buffer, rather than an instance of neovim.
- Let me open the `tasks.py` file which is driving my cmake workflow.
- Show `tasks.py`, show `:LspInfo`
- There is a python language server attached to this buffer.
- Everything I show for C++, except for clang-format and clang-tidy will work
  here as well.
- Show `<leader>lds` for symbols in the current project
- Show `do_config()`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Multi-language setup

The same setup works whether you're working on Rust, Golang,
JavaScript/TypeScript, Zig, etc...

Note:
- So those were all the demos I wanted to show.
- I'll switch over to the slides now.
- Close carnac

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Debugging

- Gdb
  - Talks by **Greg Law** from CppCon, search on YouTube
  - Back to Basics - Debugging by **Mike Shah**, CppCon 2022
- [Debug Adapter Protocol][dap]
- [nvim-dap][nvim-dap]

[dap]: https://microsoft.github.io/debug-adapter-protocol/
[nvim-dap]: https://github.com/mfussenegger/nvim-dap

Note:
- One thing you may have noticed is that I didn't cover visual debugging using
  Neovim.
- This is primarily because I use gdb whenever I need to debug a task.
- There are some really good talks on gdb by Greg Law, including one on Friday,
  and there was a talk by Mike Shah yesterday.
- But like LSP, there is something called the Debug Adapter Protocol and there
  is a plugin called `nvim-dap` which can provide visual debugging.
  - I haven't tried it out, so I'm not going to be covering it here.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- ~Context~
- ~Command Line Environment~
- ~C++ Workflows with Neovim~
- Neovim Setup <!-- .element: class="fragment grow highlight-green" -->

Note:
- Alright we're almost at the final stretch here.
# Pause for questions
