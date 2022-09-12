<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Context

- Vim
- Vim ▶️ Neovim
- Neovim today

Note:
- Let us setup the context around why this talk is on Neovim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
![Quit Vim](slides/res/quit-vim.png)

Note:
- I'm sure everyone here has already heard of Vim
- A lot of people's first interaction with Vim is accidental, you know they
  probably ran `git commit` and immediately got trapped inside of a black
  screen where the cursor isn't even blinking, and the keys don't seem to work.
- This is a bit amusing to me, because from where I stand there is a very good
  reason for this...
- And it is not Vim's fault.
- If my git commit theory is correct this happens because of the mismatch
  between the defaults of git and vim.
- Let me explain...

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Modal Editing

- Insert mode
- Normal mode
- <!-- .element: class="fragment" -->
  `i`, `o`/`O`, `a`/`A` for _Normal_ -> _Insert_ 
- <!-- .element: class="fragment" -->
  `Escape` for _Insert_ -> _Normal_
- <!-- .element: class="fragment" -->
  `:` (colon) for _Normal_ -> _Command_ 
- <!-- .element: class="fragment" -->
  - `:write`
  - `:quit`
  - `:wq` in short

Note:
- Vim's key innovation, which it inherits from Vi, is that it's a modal editor.
- When we press keys on the keyboard and corresponding letters appear on
  screen, that happens in Insert mode.
- But when we launch Vim, we're in Normal mode by default.
  - In Normal mode we speak the Vi language to interact with the Editor as
    a whole
  - And we're operating at more than a character level granularity.
- We can press one of these keys in Normal mode to go into Insert mode and then
  type whatever we want.
- We have to press Escape to come out of Insert mode and back into Normal mode
- And to quit Vim, we have to go into Command mode by typing a `:` (colon) and
  then give the command `wq`, which is short for `write` this file and `quit`
  vim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### All things vim

https://github.com/mhinz/vim-galore

Note:
- I'll not be covering the Vim language in this talk.
- This is the best resource I've found to understand Vim comprehensively.
- What I will say is that if you are learning vim on purpose, what happens
  after a while is that you develop muscle memory to interact with the editor.
  And before you know it, your brain is doing it passively while you focus on
  the code actively.
- So apart from getting out of the way visually, it also does that for your
  attention span.
- There is a reason Vim keybindings are available as a feature in almost every
  other editor I'm aware of, including all the Web Browsers via plugins.
- So if Vim is so good, then why is this talk about Neovim?
- Well I personally don't see Neovim as a completely different thing from Vim,
  like Notepad++ was for me.
- And I'm not being diplomatic here. When you see me talk about a lot of the
  features of Neovim, I organically use statements like "this is a built-in vim
  keybinding" or a "standard vim feature", even though I'm using Neovim. And
  that is because of the Vim lineage.
- But for the technical reasons we'll have to revisit the history a bit

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Vim 2013

- <!-- .element: class="fragment" -->
  Vim + [Syntastic][syntastic]
- <!-- .element: class="fragment" -->
  Save file -> Compile -> Show errors inline
- <!-- .element: class="fragment" -->
  `:w` --> Freeze
- <!-- .element: class="fragment" -->
  Not concurrent

  - Plugins run in UI thread

[syntastic]: https://github.com/vim-syntastic/syntastic

Note:
- Well, in 2013 I was using Vim with Syntastic plugin to see errors in C++ code
  inline in the editor
- And the way it worked was, everytime I saved the file, the editor would
  freeze while the compiler ran in the background, waiting for it to finish.
- As you can imagine, this was a very disruptive workflow.
- Needless to say, I was always keeping an eye out for solutions.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim

- Announced by [Thiago de Arruda][tarruda] in Jan. 2014

  - Modular/Extensible [fork of Vim][tarruda-vim]

  - Neovim core + [msgpack][msgpack] protocol for UIs

- <!-- .element: class="fragment" -->
  `0.1.0` released Nov. 2015

- <!-- .element: class="fragment" -->
  Vim 8.0 released Sept. 2016 (async support)

[tarruda]: https://github.com/tarruda
[tarruda-vim]: https://github.com/tarruda/vim/tree/3ee76edb7af5d82c551194cd2026fd7ab92fc404
[msgpack]: https://msgpack.org/

Note:
- Neovim was announced by Thiago in 2014 after his efforts to add async support
  to Vim got stalled.
  - You can still visit that link to see his original fork of Vim from 2014
    with async support
- Its essentially a Vim fork designed with modularity and extensibility in mind
- There is Neovim Core with a `msgpack` based protocol for UIs to interact with it.

Even though Vim eventually added support for async jobs next year, for some
reason...

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim

![You had me at Async](slides/res/jerry-mcguire-async.jpg)

Note:
... I was definitely sold on the idea of Neovim, even though I didn't adopt it
immediately.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim Today

- `Lua` scripting
  - `luajit` is fast 🚀
  - `vimscript` still supported
- <!-- .element: class="fragment" -->
  [Tree-sitter] support 🌲
  - syntax highlights
  - semantic textobjects
- <!-- .element: class="fragment" -->
  LSP client written in `Lua` 💡
- <!-- .element: class="fragment" -->
  `Lua` plugins
  - Feel native ✈️
  - LSP aware 🛸

[tree-sitter]: https://tree-sitter.github.io/

Note:
- A key decision Thiago made with Neovim was to use `lua` as the scripting
  language, even though `Vimscript` would still work.
- This turned out to play a huge role as plugins written in `lua` feel like
  they are a core part of Neovim.
  - They have access to all the same neovim core apis as the native Neovim
    UIs...
  - ... and they can access the language server to provide a richer feature
    set.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->

![Most loved IDE](slides/res/so-dev-survey-neovim-brave_20220908_113601_mby7MzyCMR.png)
Stack Overflow [Developer Survey 2022][so-dev-survey-2022]

[so-dev-survey-2022]: https://survey.stackoverflow.co/2022/#section-most-loved-dreaded-and-wanted-integrated-development-environment

Note:
- Its no wonder that Neovim came out as the most loved IDE in this year's Stack
  overflow developer survey, which was the 2nd consecutive year for this
  position.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Agenda

- ~Overview~
- ~Context~
- Command Line Environment <!-- .element: class="fragment grow highlight-green" -->
- C++ Workflows with Neovim
- Neovim Setup

