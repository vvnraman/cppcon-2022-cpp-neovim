<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-chapter-intro-1280x720.png" -->
## Neovim setup
- Neovim config
- Vim ➡️ Neovim
- Lua

Note:
- Lets talk about how you may get started with Neovim

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Neovim config

Under `$HOME` on Linux, `%USERPROFILE` on Windows
```console
📂 .config
└──📂 nvim
   ├── 📄 init.lua ⬅️ 
   └── 📂 lua
       └── 📄 weekend.lua
```

- Write from scratch
  - `require("weekend")` in `init.lua`
- [kickstart.nvim][kickstart]
- [lsp-zero][lsp-zero]
- [LunarVim][lunarvim]
- [NvChad][nvchad]

[kickstart]: https://github.com/nvim-lua/kickstart.nvim
[lsp-zero]: https://github.com/VonHeikemen/lsp-zero.nvim
[lunarvim]: https://github.com/LunarVim/LunarVim
[nvchad]: https://github.com/NvChad/NvChad

Note:
- When you launch Neovim, it reads this config file present at
  `.config/nvim/init.lua` inside of your `$HOME` folder.
- I'll highly recommend the `kickstart.nvim` project to get started with
  a minimal config.
- But if you were to do this from scratch, maybe allocate a weekend before you
  proceed.
  - Btw that `require("weekend")` will include the `weekend.lua` file in
    `init.lua`
- There is also this more feature rich `lsp-zero` project which includes a few
  extra things.
- And if you don't want to spend any time configuring anything, then I'll
  suggest these Neovim distributions

  - either LunarVim
  - or NvChad

  which include the kitchen sink and come with their own set of configurations
  and keybindings.

<!-- next slide -->


<!-- .slide: data-background-image="slides/res/cppcon-bloomberg-dark-content-1280x720.png" -->
### Vim ➡️ Neovim

- Use Vim for years
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
  started with just these 3 lines
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

- Declare local variable
- Set function to be called when key pressed
- Lua automatically creates closure as local variable used within function

Note:
- I'm plesantly surprised with how simple it was for me to pick up lua, without
  any experience with it prior to using Neovim.
- Its a very small and simple language with a wide acceptance already as an
  embeddable language. Its used in `redis` for scripting.
- Here is the keybinding I created to show all the symbols in the current file
  via telescope, as I showed earlier.
  - **Note in slide**
  - This is very understanable.
- And I never considered writing my own plugin in Vimscript when I was using
  Vim, but I do see myself doing something with `lua` to extend Neovim.

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
