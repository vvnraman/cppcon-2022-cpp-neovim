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
- Then I'll introduce the command line setup I typically use for C++ using
  a toy project.
- Then we'll spend a lot of time on C++ Workflows with Neovim in that toy
  project.
- Finally we'll see how one could get started with setting up Neovim to have
  a similar workflow
- I'll pause at a few places during the talk for questions, so please take
  a note of the slide numbers if you want to ask something.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
LSP & Language Server

![Language Server](slides/res/language-server.drawio.transparent.svg)

Note:
- One of the key developments over the past 6 years which enables most of the
  rich editing experience I'll be covering today is the Language Server
  Protocol
- A language server is a language specific server which understands your
  project on at a syntactic and semantic level.
  - Its analogous to a build system, and we'll see later how the C++ build
    system helps us setup the language for us, which is the de facto C++
    language server.
- So a development tool, like Neovim, can talk to the langauge server over LSP
  and ask for something like

  - "where is this function defined" or
  - "where is this type declared"

  and use that information to provide intellisence.
- Neovim has a built in LSP client which enables it to have intellisence like
  you would expect from any IDE.
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
- By the end of this talk I hope to have shown what a modern command line based
  development environment could look like, as an alternative to a GUI based
  IDE.
- I hope to show
  - Neovim's TUIs, which stands for Terminal User Interface
  - Its built in LSP integration
  - as well as its rich plugin ecosystem, a lot of which are LSP aware and leverage the
    language server for their functionality.
- Along the way you will also see a few things under the hood of the editor,
  i.e. the compiler and the rest of the tooling which are usually hidden when
  you're using an IDE.

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
- I'm using Ubuntu 20.04 running within WSL2 on Windows for this talk.
- Everything I'm showing here should work on any flavour of linux as well as
  MacOS.
- I am going to assume some C++ knowledge, and some CMake knowledge, as this is
  a talk primarily about how the many different tools invovled in C++ work
  together.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- Context <!-- .element: class="fragment grow highlight-green" -->
- Command Line Environment
- C++ Workflows with Neovim
- Neovim Setup

