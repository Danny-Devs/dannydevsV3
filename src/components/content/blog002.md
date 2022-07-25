# Why Vue 3 is Poised for a Golden Age

## From Options to Composition

Why did Vue introduce the radically different Composition API with Vue 3? The simple answer is that the Composition API affords powerful patterns and paradigms that the Options API does not.

The Options API does have its benefits. It provided a built-in way for organizing code that was particularly helpful for less experienced devs. However, the Options way of importing/exporting JS into Vue components via "mix-ins" had some critical disadvantages when compared to doing things the "normal" Javascript way (the way that Vue 3's Composition API uses...and also React, Svelte, Solid). For more on this, check out the Vue doc's [Composition API faq](https://vuejs.org/guide/extras/composition-api-faq.html).

It is important to note that Vue 3 was able to integrate the Options API on top of the Composition API to allow for *both* options to co-exist. Vue even back-ported the Composition API to Vue 2! Vue's commitment to DX means that when breaking changes happen, Vue will take steps to make the transition as smooth and easy as possible.

## Composables and composition

React's custom hooks are a powerful feature that allows *stateful*  composable JS web development. Vue 3's Composition API does the same, opening up endless possibilities for use cases.

Example:
- [vueUse](https://vueuse.org/), a collection of Vue composition utilities, or utility composables. Created by the amazing Anthony Fu, vueUse consists of Javascript programs that abstract away lower-level web APIs while tapping into Vue's reactivity system to provide you with useful reactive data and functions. Now you can implement an array of non-trivial features with just a few lines of code!

## The syntax is better than ever

The Composition API has settled on a modern syntax that looks very much like the best parts of both React and Svelte.

Writing JS inside of a script tag in Vue 3 is very much like writing JS inside of a regular .js file. Writing JS in Vue 2 was not as "normal".

Vue's SFCs (single file components, or .vue files) contain a script block, a template block, and a style block, much like Svelte. I personally love the decision to include CSS style blocks in SFCs because I experienced how painful it was to do CSS in React. The sheer number of choices available meant having to spend precious time researching them in order to pick winner. With Vue, you can just use CSS the built-in way, or you can install and use a CSS framework such as Tailwind, Bootstrap, Unocss, etc.

## A few speedbumps along the way

Vue 3's latest syntax is arguably best-in-class, relying on both the intuitive mental model of SFCs as well as the flexibility and power of a blank Javascript slate to code on. However, this syntax did go through some changes before becoming the current "script setup" syntax. It's a bit of a pain point, since the documentation may take a while to update, and there is now more than one way of doing things, but the only way to never make changes is to be perfect in the first place, which is impossible! I don't mind pain points that are a fact of life; it's the pain points that arise due to a misalignment of values between software creators and web developers that bother me...

## Elegant first-party tooling

One of the severe pain points of the decision to designate React as a library instead of a framework was the resulting overabundance of choices for core services like routing or state management. Researching the options in order to make a wise choice can eat up lots of time.

Vue's decision to embrace the label of "framework" means that it saves you tons of time. Routing and state management are high quality first-party tools that you can install with ease.

Pinia, Vue 3's state management package, is incredibly easy to work with. I left React just before I was about to learn Redux, but I was able to go through a Redux setup tutorial. It was 1000x more painful than setting up Pinia. I can only imagine what it would be like working with Redux's (and React's) Byzantinian architecture.

## Modular/extensible architecture

The way Vue is architected seems to me to follow best practices. The modular-friendly design allows rich creativity in designated places, such as plugins and other add-ons. As I become more and more of a Vue power user, I appreciate this more and more.

## Super-powered starter templates

At first I was intimidated by all the bells and whistles on Anthony Fu's [Vitesse](https://github.com/antfu/vitesse) starter template when I first used it for a new project. So I created my own template, [Vuesque](https://github.com/Danny-Devs/vuesque), adding tools like Tailwind and DaisyUI to it. After using Vuesque for a while, I noticed that I could really use some more features and functionality. I saw that Vitesse had them, so I began to add them one by one into Vuesque. Eventually, I ran into issues trying to install file-based routing on a Vuesque-based project, so I decided to go back and give Vitesse another try. This time I tried [Vitesse-lite](https://github.com/antfu/vitesse-lite), a lighter version of Vitesse.

I really enjoyed Vitesse-lite, but then noticed that Vitesse had a feature I wanted (Markdown, which I'm using right now as I type this!). And now I'm right back to where I started, using Vitesse--only now I know how most of it works and understand how to use its many superpowers.

## It's fast and light

Currently, according to my own estimation based on various articles, tweets, and tests that I've read, Vue is pretty fast and pretty light.

Size-wise, Svelte compiles away everything so it's the lightest in size. React is on the heavier end of things. Vue 3 has also gotten considerably smaller from Vue 2.

Speed-wise, Solid is the fastest. Svelte and Vue are actually pretty close in speed. React is generally slower than Vue. Vue 3 is also significantly faster than Vue 2.

## It's already the #2 JS framework

The job market for Vue developers is great. React has the biggest share of the job market, followed by Vue, with Svelte still tiny in comparison.

## Summary

It is for these reasons that I think Vue has already begun its Golden Age. Evan You, creator of Vue, recently said that there won't be any major updates for a while. This means that the Vue team can focus on optimizing Vue 3, making it smaller, faster, more stable, and more powerful.

Granted, Evan has said that Vue is experimenting with a non-v-dom, compiled strategy, codenamed Vue Vapor. However, releasing Vue 3 took several years, so my hunch is that Evan will be content take his time with Vapor and make sure they get it right.

This means that when Nuxt 3 and Vuetify 3 are *finally* released, the major parts of the Vue 3 ecosystem will be in place. Frankly though, Vitesse seems to be a sort of unofficial Nuxt 3 in that Vitesse appears to have near feature-parity with Nuxt! And now that I know the how a Vue/Vite project is structure and configured, I'm not that eager to deal with Nuxt 3's structure/configuration, because the Nuxt team has abstracted away a lot of things and installed their own custom "plumbing".

To sum it up, I'm a happier, more productive, and more powerful developer with Vue. Word will get around and the ecosystem and community will expand and mature. I give it six months to a year before we'll see more and more people recognizing how amazing Vue 3 has become.
