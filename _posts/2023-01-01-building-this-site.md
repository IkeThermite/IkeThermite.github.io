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
- To include a picture:
  - Copy the picture into the ``assets`` folder.
  - Include the HTML code below into the post.

```html
<div class='figure'>
    <img src="/assets/example.jpg"
         style="width: 100%; display: block; margin: 0 auto;"/>
    <div class='caption'>
        <span class='caption-label'>Figure 1.</span> I find this meme oddly comforting.
    </div>
</div>
```
<div class='figure'>
    <img src="/assets/example.jpg"
         style="width: 100%; display: block; margin: 0 auto;"/>
    <div class='caption'>
        <span class='caption-label'>Figure 1.</span> I find this meme oddly comforting.
    </div>
</div>

- When encountering trouble with the rendering of mathematics, refer to [this](https://stackoverflow.com/questions/49970549/trouble-rendering-some-latex-syntax-in-mathjax-with-jekyll-on-github-pages) answer.
  - Most likely, I need to escape any underscores inside my inline mathematics.

#### To Test Locally

- Open the site root folder in Git Bash.
- ``exec jekyll serve``
  - This builds the site and hosts it locally to ``http://127.0.0.1:4000/``.
  - Saving any edits will rebuild the site, but you still need to refresh the browser to see the changes.

#### To Push the Changes to the Web

- Open the site root folder in Git Bash
- The site root folder is already a Git repository with the correct name to work with Github Pages.
  - ``git add --all``
    - Stage all the changes.
  - ``git commit -a -m "Commit message``
    - Commit all the changes.
  - ``git push origin master``
    - Push the changes to the remote repository on Github.
    - This should build the site automagically!
