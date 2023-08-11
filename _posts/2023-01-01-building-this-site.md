---
layout: default
title:  "How to Build this Site"
usemathjax: true
---

I update this site fairly infrequently and thus I keep forgetting how to do it. So this is a step-by-step recipe.

This is a [static site](https://en.wikipedia.org/wiki/Static_web_page) built using [Jekyll](https://jekyllrb.com/).

#### To Edit the Site

- Open the site root folder in VS Code. 
- All the pages are markdown files kept in the root folder.
- All the posts are markdown files kept in the ``_posts``. 
- I'm using the [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) extension for editing markdown files in VS Code.
- When writing a new post, just mimic the headers of the previous posts.

#### To Build Locally

- Open the site root folder in Git Bash.
- ``exec jekyll serve``
  - This builds the site and hosts it locally to ``http://127.0.0.1:4000/``.
  - Saving any edits will rebuilt the site, but you still need to refresh the browser to see the changes.