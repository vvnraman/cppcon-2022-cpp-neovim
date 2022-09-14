<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- Overview
- Context
- Command Line Environment
- C++ Workflows with Neovim
- Neovim Setup

Note:
- This is what we'll be covering today.
- After a brief mention of some housekeeping items...
- I'll setup the context around why this is a talk on Neovim as opposed to Vim.
- Then I'll talk about the command line setup I typically use for C++ using
  a toy project.
- Then we'll spend a lot of time on C++ Workflows with Neovim via some live demos.
- Finally we'll see how one could get started with setting up Neovim to have
  a similar workflow
- I'd prefer to take questions at the end of the talk.
- So please take a note of the slide numbers on the bottom right corner if you
  want to ask something at the end.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
LSP & Language Server

![Language Server](slides/res/language-server.drawio.transparent.svg)

Note:
- One of the key developments over the past 6 years which enables most of the
  rich editing experience I'll be covering today is the Language Server
  Protocol
- A language server is a language specific server which understands your
  project at an abstract syntax tree and semantic level.

  - Its analogous to a build system, and we'll see later how the C++ build
    system helps us setup the language for us, which is the de facto C++
    language server.

- So a development tool, like Neovim, can talk to the langauge server over this
  protocol and ask for things like

  - "where is this function defined" or
  - "where is this type declared"
  - "Do you have any completion items for me at the current cursor location"

  and then use that information to provide intellisense.
- Neovim can do this because it has a built in LSP client which enables it to
  have intellisence like you would expect from any IDE.
- You don't have to fully understand this to make sense of this talk. I'll just
  be using the terms LSP and language server throughout the talk.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Goals

- Command line environment as alternative to IDEs
- Demonstrate Neovim's
  - TUIs (Terminal User Interface)
  - LSP integration
  - Rich plugin ecosystem
- Peek behind the curtain

Note:
- I hope by the end of this talk, the command line feels a bit more friendlier
  than before.
- Whether you consider it as an alternative to GUI based IDEs comes down to
  preferences.
- I also hope to show
  - Neovim's fancy Terminal User Interfaces
  - Its built in LSP integration
  - as well as its rich plugin ecosystem, a lot of which are LSP aware and
    leverage the language server for their functionality.
- Along the way we'll also peek at a few things under the hood of the editor,
  which are typically hidden away from us when we're using an IDE.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Scope

- Assumes

  - C++ knowledge
  - CMake
  - VCPKG

- Environment

  - `Ubuntu 20.04` under WSL2/Windows
  - Should work the same
    - Any Linux distribution
    - MacOS

Note:
- I am going to assume some C++ knowledge, and some CMake knowledge, as this
  talk is primarily about how the many different tools invovled in C++ conding
  work together, as opposed to focusing on any one tool.
- I'm using Ubuntu 20.04 running within WSL2 on Windows for this talk.
- Everything I'm showing here should work on any flavour of linux as well as
  Mac.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- Context <!-- .element: class="fragment grow highlight-green" -->
- Command Line Environment
- C++ Workflows with Neovim
- Neovim Setup

Note:
- Let us setup the context around why this talk is on Neovim.

