# Web dev links:

Find everything from handy utilities to supercharged tools for web design and development.

## Templates

[Vitesse](https://github.com/antfu/vitesse) is a Vue project starter template jam-packed with the latest and greatest:
- ##### Vue 3, Vite 3, pnpm
    [Vue 3](https://vuejs.org/), in my opinion, is the best overall framework out there right now. You can build a career on it (the job market is great for Vue devs), it is battle-tested, has a team behind it that believes in pragmatism and DX. For more on my thought on Vue 3, check out this <router-link to='/'>blog post</router-link>.
    [Pnpm](https://pnpm.io/) is like npm, only it stores all your node modules in a central location on your computer so that all your pnpm projects can share and use the same packages.

It contains everything from auto-importing components and Vue functions to Unocss.

By default, Unocss allows you to use Tailwind, Windi CSS, Bootstrap, and/or Tachyons utility classes! Using the Attributify preset, you can write your utility classes *directly* in an html tag as attributes--so convenient!

[Vitesse-lite](https://github.com/antfu/vitesse-lite) is a lighter version of Vitesse that drops a few features like markdown support and i8n. Check out each template's specs and pick the one that suits your project needs better.

## Metaframeworks

[Quasar](https://quasar.dev) is a metaframework that can target not only web but also mobile (through Ionic Cordova/Capacitor) and desktop (Electron). It also comes with a full-featured UI/component library as well as utility classes. It has been on Vue 3 for a while now. The documentation is solid!

[Nuxt](https://v3.nuxtjs.org/) is a metaframework built on top of Vue. It's currently a release candidate--almost ready for production. Interestingly, I find that the Vitesse template already contains many of Nuxt 3's features, even static site generation via a Vite plugin! When Nuxt 3 comes out though, I will be checking it out for sure, as I'm sure it has many cool unique features.

## Web/App Icon Image Generator

[PWAbuilder Image Generator](https://www.pwabuilder.com/imageGenerator) creates app icon sets for mobile and Windows. Provide a 512x512 or larger square PNG and the Image Generator will spit out a zip file with complete icon sets of varying resolution for each chosen platform.

## Backend

[json-server](https://www.npmjs.com/package/json-server) is a fake REST API server for testing and prototyping. Spin up the server in VSCode and voila! you can interact with it as though it were a public API--but the 'database' is simply a db.json file in your front end project's root directory!
