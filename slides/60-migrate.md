<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Neovim setup
- Neovim config
- Vim ➡️ Neovim
- Lua

Note:
- Lets talk about how you may get started with Neovim
- First we'll cover what one might do if they're coming to Neovim from any
  other editor apart from Vim.
- Then we'll talk about how an existing vim user would give Neovim a try.
- And finally we'll talk a bit about `lua`

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim config

Under `$HOME` on Linux, `%USERPROFILE` on Windows
```console
📂 .config
└──📂 nvim
   └── 📄 init.lua ⬅️ 
```

- [kickstart.nvim][kickstart]
- [lsp-zero][lsp-zero]

[kickstart]: https://github.com/nvim-lua/kickstart.nvim
[lsp-zero]: https://github.com/VonHeikemen/lsp-zero.nvim

Note:
- When you launch Neovim, it reads this config file present at
  `.config/nvim/init.lua` inside of your `$HOME` folder.
- I'll highly recommend the `kickstart.nvim` project to get started with
  a minimal config, and then build upon it over time.
- There is also this `LspZero` project, which is a bit more feature rich then
  `kickstart.nvim`.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim config from scratch

Under `$HOME` on Linux, `%USERPROFILE` on Windows
```console
📂 .config
└──📂 nvim
   ├── 📄 init.lua ⬅️ 
   └── 📂 lua
       └── 📄 weekend.lua
```

- `init.lua` contents

  ```lua
  require("weekend")
  ```

Note:
- But if you were to do this from scratch, this is the structure I'd recommend
  so that you can do it in a modular fashion.
- That `require("weekend")` line will include the `weekend.lua` file in that lua
  folder as a module in your `init.lua`.
- This is the standard way you includes modules in lua
- If it wasn't clear, I'd recommend setting a weekend aside before you proceed
  with this option.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim distributions
- [LunarVim][lunarvim]
- [NvChad][nvchad]

[lunarvim]: https://github.com/LunarVim/LunarVim
[nvchad]: https://github.com/NvChad/NvChad

Note:
- If you don't want to spend any time configuring anything, then I'll
  suggest these Neovim distributions

  - either LunarVim
  - or NvChad

  which include the kitchen sink and come with their own set of configurations
  and keybindings.

So this is what you would do if you were coming to Neovim from any other
editor.

But if you're already using Vim, and want to try out Neovim...

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Vim ➡️ Neovim

- Use Neovim with your [existing `.vimrc`][nvim-from-vim]

  `$HOME/.config/nvim/init.vim`
  ```vim
  set runtimepath^=~/.vim runtimepath+=~/.vim/after
  let &packpath = &runtimepath
  source ~/.vimrc
  ```

- Try LSP integration, Lua plugins
- Move to `init.lua`
- 💰💰💰

[nvim-from-vim]: https://neovim.io/doc/user/nvim.html#nvim-from-vim

Note:
- If you're already using Vim and would like to try out Neovim, you can get
  started with just these 3 lines here.
- Neovim will load your existing vimrc and existing plugins.
- After a while if you do decide to stay, you can switch over to the lua based
  config.
- I personally have kept my Vim and Neovim config separate as I'd stay with
  Neovim going forward.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Lua

```lua
local telescope_builtin = require("telescope.builtin")
vim.keymap.set({ "n" }, "<leader>lds", function()
    telescope_builtin.lsp_document_symbols()
end, { buffer = bufnr })
```

- <!-- .element: class="fragment" -->
  Declare local variable

- <!-- .element: class="fragment" -->
  Set function to be called when key pressed

- <!-- .element: class="fragment" -->
  Lua automatically creates closure with local variable

Note:
- I'm plesantly surprised with how simple it was for me to pick up lua, without
  any experience with it prior to using Neovim.
- Its a very small and simple language with a wide acceptance already as an
  embeddable language. Its used in `redis` for scripting.
- Here is the keybinding I created to show all the symbols in the current file
  via telescope, as I showed earlier.
- So whats happening here is
  - I'm declaring a local variable
  - I'm setting a function to be called when those keys are pressed.
  - And `lua` creates a closure around that local variable for us.
- This is very understanable.
- And I never considered writing my own plugin in Vimscript when I was using
  Vim, but I do see myself doing more and more with `lua` to personalize
  Neovim.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim Lua resources

- - TJDevries & Bashbunni [Telescope and Neovim intro][tj-bash-telescope]
  - ![tj-bash-telescope](slides/res/tj-bash-telescope-brave_20220906_191134_yqn0GNKbc6.png) <!-- .element height="25%" width="25%" -->

- - TJDevries & Bashbunni [Neovim Lua Plugin From Scratch][tj-bash-lua-plugin]
  - ![tj-bash-lua-plugin](slides/res/tj-bash-lua-plugin-brave_20220906_191305_p2HsOJaDPH.png) <!-- .element height="25%" width="25%" -->

[tj-bash-telescope]: https://www.youtube.com/watch?v=guxLXcG1kzQ
[tj-bash-lua-plugin]: https://www.youtube.com/watch?v=n4Lp4cV8YR0

Note:
- I learnt a lot about Neovim and Lua from TJ Devries YouTube channel,
  specially the long form videos where he is teaching his friend bashbunni
  about Neovim.
- He is one of core developers of Neovim and he wrote the initial LSP client as
  well as the telescope plugin.
- And she is new to Neovim so she asks the kind of questions I would have had
  if I was getting started and thats what made those videos so useful.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### [Fennel][fennel]

- <!-- .element: class="fragment" -->
  Lisp
- <!-- .element: class="fragment" -->
  Transpiles to Lua
- <!-- .element: class="fragment" -->
  Emacs Lisp users rejoice !

[fennel]: https://fennel-lang.org/

Note:
- One interesting thing I discovered while learning lua was that there is
  flavour of lisp called "Fennel" which transpiles to lua.
- So if you're on of those people who like to configure your editor using
  a lisp, then Neovim is for you !

<!-- next slide -->

# Pause before end

<!-- next slide -->
