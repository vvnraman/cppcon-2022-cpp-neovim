# C++ Coding with Neovim

<!-- vim-markdown-toc GFM -->

* [Building slides](#building-slides)
  * [Locally](#locally)
  * [Publish to Github Pages](#publish-to-github-pages)
* [Parts of RevealJs README](#parts-of-revealjs-readme)
  * [RevealJs](#revealjs)
  * [Getting started](#getting-started)

<!-- vim-markdown-toc -->

RevealJs source for the slides of my [talk at CppCon 2022](https://vvnraman.github.io/cppcon-2022-cpp-neovim/).

## Building slides

### Locally

- Install nodejs
- `npm install`
- `npm start`

### Publish to Github Pages

The `gulpfile.js` has a few edits to make `gulp package` work. This is then
exposed via a new `npm run package` command.

- Obtain a `reveal-js-presentation.zip` file
  ```sh
  npm run package
  ```
- Switch over to the `gh-pages` branch
  ```sh
  git worktree add ../gh-pages gh-pages
  ```
- Extract zip file into gh-pages branch
  ```sh
  unzip ../master/reveal-js-presentation.zip
  ```
- Add everything to git, commit and push
  ```sh
  git add .
  git commit -m "Updated `date`"
  git push github gh-pages # github is the name of my github.com remote
  ```

---

## Parts of RevealJs README

### RevealJs

reveal.js is an open source HTML presentation framework. It enables anyone with a web browser to create beautiful presentations for free. Check out the live demo at [revealjs.com](https://revealjs.com/).

The framework comes with a powerful feature set including [nested slides](https://revealjs.com/vertical-slides/), [Markdown support](https://revealjs.com/markdown/), [Auto-Animate](https://revealjs.com/auto-animate/), [PDF export](https://revealjs.com/pdf-export/), [speaker notes](https://revealjs.com/speaker-view/), [LaTeX typesetting](https://revealjs.com/math/), [syntax highlighted code](https://revealjs.com/code/) and an [extensive API](https://revealjs.com/api/).

### Getting started
- 🚀 [Install reveal.js](https://revealjs.com/installation)
- 👀 [View the demo presentation](https://revealjs.com/demo)
- 📖 [Read the documentation](https://revealjs.com/markup/)
- 🖌 [Try the visual editor for reveal.js at Slides.com](https://slides.com/)
- 🎬 [Watch the reveal.js video course (paid)](https://revealjs.com/course)
