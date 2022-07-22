# Why Vue 3 is Poised and Ready for its coming Golden Age

## From Options to Composition

Vue 3 rightly has its detractors. There are those who say, why did Vue introduce the radically different Composition API? The reason is that the Composition API affords certain powerful patterns and paradigms that the Options API does not.

The Options API had its own benefits. It provided a built-in way for organizing code. However, mix-ins (the Options way of importing/exporting JS) had some key disadvantages when compared to doing things the "normal", more composable Javascript way (the way of Vue 3's Composition API, and also React, Svelte, Solid).

I guess in hindsight Vue had to evolve to compete. But the cool thing is that Vue 3 was able to integrate the Options API on top of the Composition API to allow for both options to co-exist. This is one example of Vue's commitment to DX.

## Composables and composition

React's custom hooks allowed for full-powered composable JS programming. Vue 3's Composition API does the same.

Example: [vueUse](https://vueuse.org/), a collection of Vue composition utilities, or utility composables. Spearheaded by the amazing Anthony Fu, vueUse consists of Javascript programs that abstract away lower level web APIs while also tapping into Vue's reactivity system to provide you with useful reactive data and functions. Now you can implement non-trivial features with just a few lines of code!

## The syntax is better than ever

The Composition API also settled on a syntax that looks very much like parts of both React and Svelte.

Writing Javascript inside of a script tag in Vue 3 is very much like writing Javascript inside of a .js file in React.

Vue 2's SFCs (single file components, .vue for Vue and .svelte for Svelte; they contain a script block, a template block, and a style block) looked similar to Svelte's except for that Vue's script block contained Options API-based JS. Now Vue 3's script block contains normal-looking Javascript.

After a speedbump or two (the latest script syntax, using 'script setup', was released some time after Vue 3's initial launch), Vue 3's latest syntax is arguably best-in-class, containing both the sound mental model of SFCs as well as the flexibility and power of a blank Javascript slate to build on.

## Elegant first-party tooling

One of the severe drawbacks of the vision of React as a library was the overabundance of choices available for core services like routing or state management. Researching the top two or three choices alone required spending time in each one's documentation.

One of the huge wins of the vision of Vue as a framework is that routing and state management are high quality first-party tools.

Pinia, Vue 3's state management package, is a breeze to setup, hook into and work with. I left React before learning Redux, but I did go through a Redux setup tutorial, and it was 1000x more painful than setting up Pinia. I can only imagine what it would be like to work with Redux's Byzantinian architecture. This is part of why I am not only happeir but also more productive when I develop in Vue.

## Modular/extensible architecture

The way Vue is architected seems to me to follow best practices. The modular-friendly design allows rich creativity in designated places, such as plugins and other add-ons. As I become more experienced, I appreciate this more and more.

## Super-powered starter templates

At first I was intimidated by all the bells and whistles on Anthony Fu's [Vitesse](https://github.com/antfu/vitesse) Vue starter template when I first used it for a new project. So I created my own template, [Vuesque](https://github.com/Danny-Devs/vuesque), and added tools like Tailwind and DaisyUI to it. Then I realized that Vitesse had some features that I wanted, so I began to install them one by one into my Vuesque template. Eventually, I ran into a problem trying to install file-based routing on one project, so I decided to give [Vitesse-lite](https://github.com/antfu/vitesse-lite) a try.

I really enjoyed that, but then saw that Vitesse had a feature I wanted (markdown, which I'm using right now as I type this). And now I'm right back where I started, using Vitesse, only now I understand most of it and appreciate its many superpowers.

## It's fast and light

Currently, according to my own estimation based on various articles and tweets and tests that I've read and reviewed, Vue is pretty fast, and it's pretty light.

Svelte compiles away everything so it's the lightest. React is on the heavy end. Vue 3 has gotten considerably lighter from Vue 2.

Solid is the fastest. Svelte and Vue are actually pretty close in speed. Vue 3 is significantly faster than Vue 2. React is slower than Vue.

## It's already the #2 JS framework

The job market for Vue developers is great. React has the biggest job market, while Svelte has a tiny one at the moment.

## Summary

It is for these reasons that I think Vue is entering its Golden Age. Evan You, creator of Vue, recently said that there won't be any major updates for a while. This means that they can focus on making Vue 3 smaller and faster and more powerful.

Granted, Evan also said that they are currently experimenting with a non v-dom-based, compiled strategy codenamed Vue Vapor. However, releasing Vue 3 took several years, so my hunch is that Evan will be content to hold Vue 3 steady while making sure that Vapor breaks as few things as possible while bringing in as many cool things as possible.

This means that when Nuxt 3 and Vuetify 3 are *finally* released, the major parts of the Vue 3 ecosystem will be put in place. Though frankly, Vitesse seems to be an unofficial Nuxt 3 already, and Vuetify being a UI/component library is just one of many choices.

Keep in mind that Vue 2 is scheduled for deprecation in Fall 2023, which means the entire Vue community will soon be on the same version and probably using the Composition API.

Happier, more productive, and more powerful developers should translate to better ROI for companies. Word will get around more and more and the ecosystem will expand and mature. I would say, give it 6 months to a year, and we'll see people recognizing how amazing Vue 3 has become.
