---
layout: single
title: "Making Jekyll posts and building jekyll for github pages"
---



I need to note a few things on how this process works, because I will forget, because I'm not doing it so often. 

## Creating a new post

To create a new blog post, `cd` into your parent directory of your github pages repository, and run the following in a terminal:

~~~
> touch YYYY-MM-DD-blog-post-title.md
~~~

Edit your markdown blog post using your favourite code editor. The frontmatter (when using Minimal Mistakes theme) should look similar to:

~~~yaml
---
layout: single
title: Blog Post Title
---
~~~

Save your changes. 

## Check that it works, run a local jekyll server

This requires you to run

~~~
bundle exec jekyll serve
~~~

Then navigate to the default address `localhost:4000`. 

## A note on pushing the repository to github
I have already setup creating tokens for pushing to github. This requires that you access your *Settings -> Developer Options -> Generate tokens* or something to that effect. The instructions are there I think. Otherwise google the error your going to from terminal by pushing it the wrong way. 

Then:

~~~
git push -u origin main
~~~
