<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Command line environment

- Terminal + Tmux
- C++ Project
- Neovim

Note:
- Lets talk about the setup for C++ coding on the command line
- I'm may cover some of the parts here only briefly as its mostly for building
  familiarity with the tools I'll be working with in addition to Neovim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/cli-tmux-project_20220904_205215_ZyYpuEDIjd.png)

Note:
- This is a typical view for me when I'm working on a project using Neovim.
- What you're seeing here is a single tmux window inside of a tmux session.
- And I'll get to what `tmux` is in just a bit.
- The single tmux window with has 2 panes.
  - The top tmux pane is running Neovim
  - The bottom tmux pane is just the bash shell.
- Everything is running within Windows Terminal. You'd probably use GNome
  terminal on native Ubuntu or the Mac Terminal on a Mac.
- So `tmux` is a terminal multiplexer.
  - i.e. Rather than me having multiple Window Terminal tabs and panes, and
    runing bash within those, I let `tmux` handle that for me.
- Neovim also has its own representation of Windows and Tabs.
  - The top tmux pane running Neovim is basically a single Neovim window within
    a single Neovim tab.
  - You can have more than 1 Neovim window within a tab, and you can have
    multiple Neovim tabs.
- I'm only mentioning these things so that you can better visualize the demos
  when I get to them.
- In the next slide, you can see the keys I pressed in the top right corner
  in dark blue background

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/tmux-window-pane-neovim-Carnac_20220905_081509_VNRCxtt0c4.gif)

Note:
- I am opening another `tmux` window within the same `tmux` session.
- I split it vertically, run Neovim in the left pane and paste a "Hello CppCon"
  program.
- I switch to the right pane and run `g++` to compile it and the run it.
- So `tmux` lets me to stay within the command line environment while still
  letting me work on different things via a keyboard driven workflow.
- Both Vim and Neovim have a Terminal mode which allows you do stay completely
  within Neovim. I haven't found a reason to use it yet as I already have
  a fluent `tmux` workflow already. But if you're not used to `tmux` that that
  Terminal mode in Neovim should come in very handy.
- I'm typically always zoomed in into the Neovim tmux pane, what you're seeing
  here is just for demonstration.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### C++ Project

Toy calculator

```
📂 .
├── 📄 CMakeLists.txt
├── 📄 README.rst
├── 📂 src
├── 📄 tasks.py
├── 📂 tests
└── 📄 vcpkg.json
```

- Add 2 numbers
- Subtract 2 numbers

Note:
- I have a very simple toy C++ project which just does addition and subtraction
  on the command line.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### C++ Project

- `CMake`, `ninja`, `gcc-11`

- <!-- .element: class="fragment" -->
  `vcpkg.json`

  - `cli11`
  - `fmt`

- <!-- .element: class="fragment" -->
  `tasks.py` for [invoke][invoke]

  - Runs CMake configure, build, install

[invoke]: https://docs.pyinvoke.org/en/stable/index.html

Note:
- It uses CMake to generate the build files for ninja
- I have gcc-11 installed on the system
- and I'm using `vcpkg` to fetch the dependencies
- I'm using a tool called `invoke` to drive the development workflow and that
  is where the `tasks.py` file comes in.
  - A lot of times you may have see a `Makefile` or a shell script in a project
    to avoid having to type lengthy commands to build it.
  - `tasks.py` has the same purpose here.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### vcpkg

Setup `vcpkg` (submodule per project)

```sh
git submodule add https://github.com/microsoft/vcpkg.git
git submodule update --init
cd vcpkg
./bootstrap-vcpkg.sh -disableMetrics
```

Dependencies pinned by default

Note:
- This is just a reference slide, included here for completeness.
- I'm using `vcpkg` as a submodule in this project, and these are the steps you
  have to follow before we can use it.
- This way the dependencies remained pinned to whatever was present in the
  specific vcpkg commit I pulled.
  - So I know that the project would always build even if I take a sabattical
    from it a couple of months and those dependencies may have been updated in
    a backwards incompabitle manner upstream.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### CMake

CMake Configure using `tasks.py`

```console
# From project root
$ invoke config
```

<div class="fragment">

Roughly does the following
```sh
# create unique build dir and cd to it
cmake \
  -S path/to/project/ \
  -DCMAKE_TOOLCHAIN_FILE=path/to/project/vcpkg/scripts/buildsystems/vcpkg.cmake
```

</div>

Note:
- I used `invoke` to run the cmake configure step.
- Roughly speaking
  - It creates an out of source build directory and `cd`s into it
  - Then it runs cmake configure providing it a path to the vcpkg toolchain
    file

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### CMake

```console
📂 build
├── 📄 build.ninja
├── 📄 compile_commands.json ◀️
├── 📂 src
├── 📂 tests
├── 📂 vcpkg_installed ◀️
└── ...more...
```

- `vcpkg_installed` 📂
- `build.ninja` 📄
- <!-- .element: class="fragment" -->
  `compile_commands.json` 📄

Note:
- I used `invoke` to run the cmake configure step.
- Roughly speaking
  - It creates an out of source build directory and `cd`s into it
  - Then it runs cmake configure providing it a path to the vcpkg toolchain
    file
- Below you can see what we get in the build directory.
- The `vcpkg_installed` folder is where all the dependencies I've specified in
  `vcpkg.json` get installed.
- We also have this file called `compile_commands.json`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Compilation Database

[Json Compilation Database][ccdb]

```console
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=1 ...
# or
CMAKE_EXPORT_COMPILE_COMMANDS=1 cmake ...
```

[ccdb]: https://clang.llvm.org/docs/JSONCompilationDatabase.html

Build directory
```console
├── ...
├── 📄 compile_commands.json
└── ...more...
```

Note:
- That is a json compilation database produced by CMake if you do either of
  things as shown at the top here.
- Its a de-facto standard for passing information from the compiler to any tool
  which wants to consume it.
- I'm not getting into the details of whats in there, butI'll be happy to
  discuss that if we get time at the end.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim 🤝 Clangd

Source directory
```console
├── 📂 src
├── 📂 tests
├── 📄 compile_commands.json ⇒ path/to/build/compile_commands.json ◀️
└── ...more...
```

Note:
- All we need to make the Neovim lsp client connect to `clangd`, the C++
  language server, is to have a complation database present in the root of
  my project.
- So all I did here was run `invoke config`, and it did a CMake configure for
  me, and then it created a symlink to the `compile_commands.json` in the build
  directory.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Toy calculator

```console
 ./usr/local/bin/calc --help
A toy calculator program to demo Neovim on the command line
Usage: calc [OPTIONS] SUBCOMMAND

Options:
  -h,--help                   Print this help message and exit

Subcommands:
  add                         Add 2 numbers
  sub                         Subtract numbers
```

Add
```console
./usr/local/bin/calc add 10 5
10 + 5 = 15
```

Subtract
```console
./usr/local/bin/calc sub 10 5
10 - 5 = 5
```

Note:
- This is what you see when you run the toy program

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim

- Neovim `0.7.2`
  - Built-in LSP client 🤯
- Notable Plugins
  - [telescope][telescope]
  - [trouble][trouble]
  - [nvim-cmp][nvim-cmp]
  - [which-key][which-key]
- [packer][packer] Package manager
- [mason][mason] CLI Tools installer
  - Handles `clangd` installation

[telescope]: https://github.com/nvim-telescope/telescope.nvim
[trouble]: https://github.com/folke/trouble.nvim
[which-key]: https://github.com/folke/which-key.nvim
[packer]: https://github.com/wbthomason/packer.nvim
[mason]: https://github.com/williamboman/mason.nvim
[nvim-cmp]: https://github.com/hrsh7th/nvim-cmp

Note:
- This is mostly a reference slide
- I wanted to highlight a couple of indispensable plugins. I'll bring them up
  again as I use them in the next section.
- `mason` is the plugin which installs the language servers on behalf of Neovim
  - So we don't necessarily have to use it if we're installing language servers
    on our own.
- The primary reason for using Neovim is that you can use the Vim language to
  interact with the editor. Everything I'll be covering in the workflows
  section is just to show that you don't lose access to any IDE like features.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Mnemonics

![Mnemonics](slides/res/lojban.png)

https://xkcd.com/191/

`<Leader>` - `<Space>`

Note:
- One last thing, before I switch to demos.
- One of the things you learn to do with Vim and Neovim is to come up with your
  own mnemonics to remember keybindinds for the most common workflows.
- Vim has a concept of a `<Leader>` key which you can set to any key and it
  acts as a namespace for your own key-bindinds so that it doesn't interfere
  with any built-in keybindinds.
  - For me that is `<Space>` and I mention that because you'll be seeting that
    a lot.
- All the keys I press will show up on the top right corner.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- ~Context~
- ~Command Line Environment~
- C++ Workflows with Neovim <!-- .element: class="fragment grow highlight-green" -->
- Neovim Setup

Note:
# Pause for questions
