<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Command line environment

- Terminal + Tmux
- C++ Project
- Neovim

Note:
- I'm may cover some of the parts here only briefly as its mostly for building
  familiarity with the tools I'll be working with in addition to Neovim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/cli-tmux-project-tundra-1920x1080.png)

Note:
### CLI tmux 1

- This is a typical screen which I spend most of my time looking at when I'm
  working on a project.
- So you can imagine that I would want it to look a bit aesthetically pleasing.
- **Pause**
- I'm glad to have found that my wife likes this as well.
- **Pause**
- I recently gifted her a fancy colourful mechanical keyboard to see if I can
  nudge her in this direction.
  - Not on any special occasion, just a random surprise.
- So we'll see.
- Okay, let us break down what we're looking at.
- This is Windows Terminal running a tmux session inside Ubuntu. I'll get to what
  `tmux` is in just a bit.
- You'd probably use the GNome terminal on native Ubuntu or Alacritty or
  Wezterm or your terminal of choice.
- So we have a single tmux window with 2 panes, insdie of a tmux session.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->

![tmux project](slides/res/cli-tmux-project-neovim-focus-tundra-1920x1080.png)

Note:
### CLI tmux 2

- The top tmux pane is running Neovim
- When I'm working on code, I'm zoomed in to this pane so that I don't see any
  other panes.
- You can see that the majority of that pane is just code and there is
  a single line at the bottom with some information about that code.
  - I'm in normal mode
  - I'm on the main branch
  - The file name is `app_main.cpp`
  - Its a UTF-8 encoded c++ file
  - The cursor is on line 30, column 18

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/cli-tmux-project-bash-focus-tundra-1920x1080.png)

Note:
### CLI tmux 3

- The bottom tmux pane is just the bash shell.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### tmux - Sessions, Windows, Panes

![tmux project](slides/res/cli-tmux-project-bash-only-tmux-focus-tundra-1920x1080.png)

Note:
### CLI tmux 4

- So `tmux` is a terminal multiplexer.
- i.e. Rather than me running multiple instances of Window Terminal and then
  having a shell within those, it manages that for me.
- I'm typically always zoomed in into the Neovim tmux pane, or any other pane
  if I'm spending any significant amount of time in it.
- In the next 2 slides, I'll show a gif of this workflow in action, and you can
  see the keys I'm pressing to do everything in the top right corner.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/cli-tmux-window-pane-navigate.gif)

Note:
- I am opening another `tmux` window within the same `tmux` session.
- And then I split it vertically into 2 panes to have 2 shells.
- Next I'll do something more here

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![tmux project](slides/res/cli-tmux-pane-switch-neovim-gcc.gif)

Note:
- I switch to the left pane, open Neovim, copy paste a hello world program and save it.
- Then I switch to the right pane and run `g++` to compile it and the run it.
- So `tmux` lets me stay within the command line environment and allows me to
  multi-task via a keyboard driven workflow.
- Both Vim and Neovim have a Terminal mode which allows you do stay completely
  within Neovim. I haven't found a reason to use it yet as I already have
  a fluent `tmux` workflow. But if you're not used to `tmux` then that Terminal
  mode in Neovim should come in very handy.
- This will become more clear when I get to the demos.
- Okay, lets talk about the C++ project.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### C++ Project

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

https://github.com/vvnraman/cppcon-2022-cpp-neovim-toy-calc

Note:
- I have a very simple toy C++ project which just does addition and subtraction
  on the command line.

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
- A few things of note...

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
- It uses CMake to generate the build system, which in our case is ninja
- I have gcc-11 installed on the system
- and I'm using `vcpkg` to provide the dependencies of the project.
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
- So the first thing you have to do with CMake is to configure the project,
  which generates the build system for us.
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
- This generates the following build folder.
- The `vcpkg_installed` folder is where all the dependencies I've specified in
  `vcpkg.json` get installed.
- We also have this file called `compile_commands.json`, whats that.

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
- Its a de-facto standard for providing information from the compiler around
  how each file in the project was compiled.
- I'm not getting into the details of whats in there, but I'll be happy to
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

`$ invoke config` <!-- .element: class="fragment" -->

Note:
- So all we need to do to make the Neovim lsp client connect to `clangd` C++
  language server, is to have that complation database present in the root of
  our project.
- And all I did here was run `invoke config`, and it did a CMake configure,
  then it created this symlink in the source directory, and that made Neovim
  connect to clangd.

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
- `mason` is the plugin which installs the language servers on behalf of Neovim.
  - If it wasn't clear, `clangd` is running locally on the system, same as
    Neovim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Mnemonics

![Mnemonics](slides/res/lojban.png)

https://xkcd.com/191/

`<Leader>` - `<Space>`

Note:
- **Pause**
- One last thing, before I switch to demos.
- One of the things you learn to do with Vim and Neovim is to come up with your
  keybindings for the most common workflows, and you do that by having
  mnemonics you can remember for those keybindings.
- You can come up with whatever keybinding you want, as long as you remember
  it.
- I look forward learning other people's mnemonics to see if they have a better
  one.
- Vim has a concept of a `<Leader>` key which you can think of as a namespace
  for your own keybindings, so that they don't conflict with built-in vim
    keybinding.
- For me that is `<Space>` and I mention that because you'll be hearning me say
  `<Leader>` a lot during the demos, when I say what my mnemonics are.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- ~Context~
- ~Command Line Environment~
- C++ Workflows with Neovim <!-- .element: class="fragment grow highlight-green" -->
- Neovim Setup

Note:
- Lets me take a look at the time.
- I should have 30-35 mins left right now.

### Pause for questions
