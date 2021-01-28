---
title: How to build a blog with Hexo
date: 2020-11-11 00:37:57
tags: [tool]
categories: 
- [notes]
- [communication]
---

# Installation
1. Install node.js

    - node.js: JavaScript runtime environment and allows JavaScript to run outside of browser 
    - how to install: [download link](https://nodejs.org/en/download/)
    - version check after installation: in terminal run command `node -v`


2. Install Git

    - Git: version control system
    - how to install: [download link](https://git-scm.com/downloads)
    - version check after installation: in terminal run command `git version`


3. Install Hexo

    - Hexo: static site generator
    - how to install: in terminal run command `npm install -g hexo-cli`
    - version check after installation: `hexo -v`


# Setup

1. initialize hexo in target folder: `hexo init <folder>`

2. folder structure after installation:

    - _config.yml: site configuration file
    - package.json: application data
    - node_modules: for node.js
    - scaffolds: templates for content pages
    - source: contents
    - themes: static page themes


3. configuration:

    - details see [Hexo Configuration](https://hexo.io/docs/configuration)


# Writing

1. create a new post/page: `hexo new [layout] <title>` (layout is post by default)
2. create a new draft: `hexo new draft <title>`
3. publish drafts: `hexo publish <title>`


# Deployment using Git

1. view on local host: `hexo server`
2. install hexo-deployer-git: `npm install hexo-deployer-git --save`
3. deploy site: 
    1. `hexo clean`
    2. `hexo deploy`


# References
- [Hexo tutorial YouTube list](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOMJR6D25ishrSedvsguVSm)
- [Hexo documentations](https://hexo.io/docs/)
- [Hexo plugins](https://hexo.io/plugins/)
- [Hexo graph tutorial](https://developpaper.com/use-markdown-to-draw-graphs-in-hexo/)
- [Next theme](https://theme-next.js.org/docs/getting-started/)
