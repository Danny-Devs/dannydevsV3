---
title: Blog 001
---

# Blog 001: How I made this blog post

This post was written in [Markdown](https://www.markdownguide.org/), a simple markup language that makes writing articles faster and easier than writing them in HTML. For example, HTML often requires pairs of tags to surround content, whereas Markdown often requires just a starting "tag".

> This is a blockquote. Simply start a line with a ">", and the markdown will automatically be converted to this blockquote style.

You can ~~strike-through~~ and make things **bold** and *italic*.

For a line break, just hit return twice.

# This is an h1

## This is an h2

### This is an h3

#### This is an h4

##### This is an h5

One of the key features of markdown is the ability to easily add pre-formatted code snippets:

```js
// syntax highlighting example
<script setup>
const foo = ref('bar')

function vitesse() {
  console.log(foo.value)
}
</script>
```


It's easy to add lists, links, images too, though markdown has little control over images (I used regular old HTML for the image below--you can inline HTML and Vue components in markdown files thanks to the Vitesse starter template!).

<div w-24 mx-auto>
  <img src="/tux.avif" width="200" height="100">
</div>

And that is a whirlwind tour of markdown. In the following blogs I'll be using this interesting piece of technology to faciliate the writing of my blogs. Markdown is not something that a layperson would use, however; the person off the street would be better off using a rich text editor, which allows the user to create blog posts in a familiar word processor/Wordpress type of environment.

A CMS (content management system) can also provide user registration and authentication services. However, for my website blog, I'll be the only user, so all I need is an efficent way to write out and design my blog posts--doing this in HTML is quite a chore, since to even write body text, I would have to deal with endless p tags and manually adjusting padding/margins.

With markup, for body text, I simply type away. To add a break, I hit enter twice.

## Closing notes

At first I found markdown to be a rather esoteric and dense subject. I knew it was used for things like personal blogs, note-taking, and documentation writing because it made creating content easier.

After multiple attempts at learning markdown, I've finally come to the point where I'm 1) using it fairly fluently, 2) appreciating its merits, and 3) planning to produce regular blog content with it.

I will have to look into implementing pagination and a table of contents/navigation as the number of blog posts grows. I'm looking forward to expanding my blog developing skills! Until next time, DannyDevs out!
