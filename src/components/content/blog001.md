---
title: Blog 001
---

# Blog 001: How I made this blog post

This post was written in [Markdown](https://www.markdownguide.org/), a simple markup language that makes writing content faster and easier than with regular old HTML. For example:

- When writing paragraph content, no surrounding p tags are required. This one in particular is a huge timesaver. Markdown also often requires just one starting "tag" at the beginning of content rather than requiring that you bookend content with a pair of tags.
- Creating links in markdown is fast. Type "\[*link name*](*link url*)" and Markdown takes care of the linking and styling for you.
- Markdown is automatically formatted with configurable CSS. Set it and forget about it. It provides you with a "prose" class that allows you to target only your markdown files.
- Markdown provides built-in formatting for code snippets, but to get syntax highlighting you need an external package. The Vitesse template was using [Prism](https://prismjs.com/), but I actually [tweeted](https://twitter.com/antfu7/status/1551200894527873025) the Vitesse creator, Anthony Fu, about how I was having trouble getting Vue syntax highlighting in my code snippets (JS and HTML were working fine). Within an hour or so, he had already made a [commit](https://github.com/antfu/vitesse/commit/1f546793b79bd7b640660a55959d16d43ede1ee5) that removed Prism and added [shiki](https://shiki.matsu.io/)). I followed his changes, and voila! I now have Vue syntax highlighting for my code snippets. You can see an example below.

## Examples of Markdown

> This is a blockquote. Simply start a line with a ">", and the markdown will automatically be converted to this blockquote style.

You can ~~strike-through~~ and make things **bold** and *italic*. Though these require paired "tags" they are not actually tags with angle brackets. For example, to make something bold, you can surround it with two asterisks: \*\*bold\*\* becomes **bold**.

For a line break, just hit return twice! No need to add a \<br> tag or otherwise adjust spacing.

# This is an h1
(just start the line with a #)

## This is an h2
(start the line with 2 #'s)
### This is an h3
(start with ###)
#### This is an h4
and so on.
##### This is an h5

---
## Code snippets and Syntax Highlighting
One of the key features of markdown is the ability to easily add pre-formatted code snippets with language/domain-specific syntax highlighting.

This is what a code snippet looks like with no syntax highlighting:

```
//syntax highlighting example
<script setup>
const foo = ref('bar')

function vitesse() {
  console.log(foo.value)
}
</script>

<template>
  <div>Hi there!</div>
</template>

<style scoped>
  p {
    color: pink;
  }
</style>
```

Here's the code snippet with syntax highlighting specifically for Vue:

```vue
// syntax highlighting example
<script setup>
const foo = ref('bar')

function vitesse() {
  console.log(foo.value)
}
</script>

<template>
  <div>Hi there!</div>
</template>

<style scoped>
  p {
    color: pink;
  }
</style>
```

Much nicer, isn't it?

To add a code snippet, surround the snippet with \``` and \```. After the beginning \```, you can add meta information to have Shiki provide the appropriate syntax highlighting. In this case I'm using Vue, so I  added "vue" after the opening \``` (as in \```vue). You can easily swap in VS Code themes into Shiki with a bit of configuration.

It's also easy to add images:

<div w-24 mx-auto>
  <img src="/tux.avif" width="200" height="100">
</div>

I used regular old HTML in my markdown file for the image. You can even use Vue components in your markdown files too! I'm quite curious to see what cool patterns might emerge from utilizing this capability.

---
## Closing notes

And that is a whirlwind tour of markdown. I'll be using this interesting piece of technology to faciliate the writing of my blogs. Do note that Markdown is probably not something that a layperson would use; the person off the street may be better off using a rich text editor in a CMS (content management system), which allows the user to create blog posts in a familiar word processor/Wordpress type of environment.

A CMS can also provide user registration and authentication services. However, since I don't need those things at this time (I might eventally, if I want to add a comments feature that will require readers to create an account and log in), what I need is an efficent way to write out and design my blog posts.

Indeed, I found Markdown to be a rather esoteric and dense subject. The syntax has a relatively easy learning curve, but you have to learn other things, such as how to integrate Markdown into your website, how to implement syntax highlighting, and how to adjust your config/settings. I finally have a good grasp on it all, after numerous attempts to understand it and use it.

This echoes something that web dev has taught me time and time again. Some things will take multiple concerted attempts before they will make any kind of sense to you. If you need to learn something, attack it with the same intensity, but let your patience quiet any early discouragement.

Looking ahead, I will be exploring pagination and table of contents/navigation as the number of my blog posts grows. Until next time, DannyDevs out!
