# Become a Web Jedi with Vue 3

> Note: this article assumes foundational knowledge of HTML, CSS, and Javascript

The way to become a web jedi is to wield your tools in an increasingly skillful way. Fighting with your tools because they are overcomplicated,  limited by core architectural decisions they've made in the past, or suffer from poor good developer experience is **not** what you want to experience as a jedi-in-training.

I have found that using a Vue starter template (specifically, the [Vitesse](https://github.com/antfu/vitesse) template) saves me a great deal of setup time and contains features that enhance my productivity and allow me to focus on building things, which is what web jedis do.

Vitesse's added features are listed below, along with a brief description of why they are so useful:

## Vitesse features

- **file-based routing**

  File-based routing is an intuitive approach to routing that uses folder structure to automatically create routes (and handle other routing duties such as catching all urls or handling dynamic routes). It saves time from having to manually handle routing with Vue Router.

- **layouts**

  Layouts are stored in the `layouts` folder, and are useful for things such as a "404" layout designated for displaying 404 errors, or a "home" layout designated for the home view, or any other custom layout. This plugin provides a design capability that IMO most projects will benefit from.

- **Pinia installed**

  The official state management solution, Pinia, is pre-installed. Pinia is extremely easy to learn and use thanks to its simplicity and elegance. Thus, Vue practitioners find themselves asking, "How does global state fit into my project?" rather than say trying to avoid working with global state management because it involves having to learn a complicated new library. With Pinia, Vue devs can start learning about the pros and cons of global state management from Day 1.

- **auto-importing of components**

  This one is just a major DX quality-of-life feature. This plug-in looks at folders (this is configurable) and auto-imports any of the components within them when you use them in your scripting. In other words, it saves you a ton of typing and mousing and let's you focus on coding.

- **unocss**

  This feature was a slow burn for me. I was still using Tailwind in my non-Vitesse projects, but when I jumped into Vitesse I had to begin learning how to use [unocss](https://github.com/unocss/unocss). It was easy because unocss's default preset contains Tailwind utility classes (as well as Windi CSS, Tachyons, and one other framework), so in the template it was a lot like using Tailwind. Only now, with the Attributify preset also added, I could write Tailwind classes without the `class=""`, as though they were literally attributes of the HTML tag! Ingenious. Unocss is able to somehow pick and choose which features to use, because it adopts Windi CSS's shortcuts syntax, only we put it in the vite.config file.

```ts
// vite.config.ts
import Unocss from 'unocss/vite'

export default {
  plugins: [
    Unocss({
      shortcuts: {
        // shortcuts to multiple utilities
        'btn': 'py-2 px-4 font-semibold rounded-lg shadow-md',
        'btn-green': 'text-white bg-green-500 hover:bg-green-700',
        // single utility alias
        'red': 'text-red-100'
      },
    }),
  ],
}
```

- **markdown**

  Anthony added markdown capabilities to Vitesse based on the npm packages markdown-it, a markdown parser, and shiki, which provides the syntax highlighting for the code blocks. Markdown is great for writing things like blog posts, documentation, and coding tutorials--the syntax is more efficient to work with than HTML. You can use HTML in .md files, and even import Vue components as well! I currently use a .vue file as a wrapper for my .md files, but now I'm thinking it might be wise to use .md files (which are read as pages by the file-based routing plug-in) as wrappers, and add HTML (such as images--markdown does NOT provide much control over images) or Vue components (super dynamic markdown pages!) as needed or desired.

- **SSG**

  SSG stands for static site generators, which support server side rendering to make your apps faster. Anthony added an SSG plugin, so I assume that it worked with Netlify to make this very website, dannydevs.com, a statically generated website. I recently checked my Lighthouse score and everything was in the 90s, green. As I grow my website, I'm curious to see how my Lighthouse scores progress.

- **PWA**

  I opened dannydevs.com in my phone browser as soon as Netlify had deployed it in order to see how my site really looked on mobile. I was very pleased to see that it looked even better on mobile than it did in Chrome dev tools' responsive mode. I also noticed a popup that asked me if I wanted to install the website as an app on my home screen. This is what the PWA plugin enables! Super cool. I have to check if my app "actionator" has the PWA plugin installed, because that would be something I'd like to have. A quick tap and I can do a quick UX session as needed.

- **I18N**

  This plugin will be of interest to those who want to incorporate things like language modes into their site. Makes sense since Anthony Fu is Chinese. I was unfamiliar with I18N before, and it was quite fascinating to see how it was implemented. I18N apparently spits out a "t" function that you surround text with, and it translates that text according to what language mode is selected.

- **dark mode**

  This feature is implemented using one of the many vueUse composable utilities. What's great is that the `composables` folder is watched and auto-imported as well!

## Next Steps

To set up the template as a new project, I would recommend using [degit](https://github.com/Rich-Harris/degit). It is quicker than `git clone` because it doesn't download the repo's entire git history). Create a new folder and give it your project name. Degit will clone the Vitesse template into this folder. Make sure you are in this folder on the command line (you can type `pwd`, "print working directory", to check).

> Tip: I like to open my command prompt from a folder by right-clicking and selecting "Cmder here". This will conveniently open up a Cmder console window with that folder as the working directory. I'm on a Windows machine. I use [Cmder](https://github.com/cmderdev/cmder) rather than the built-in Command Prompt or Powershell because it recognizes Unix Bash commands and looks nice.

So from your project folder, degit Vitesse in the terminal: `degit antfu/vitesse`

Voila! You have a brand new Vitesse starter project ready to go. I would suggest setting your project up with git/Github, then immediately deploying it onto the web (I happen to use Netlify, but there's also Vercel and others). Netlify looks at your Github repo, and when it changes, re-builds your website and attempts to deploy the new build. If it fails, it errors out; if it succeeds, your website is now updated to that particular Github commit.

Now, you can focus on tinkering and building: creating nav bars, footers, and other UI components; creating pages, layouts, and content; and designing and developing interactions, data flow, and app architecture.

Make many websites! I'd encourage you to do tutorials and experiments on a personal website, so that you can document your work while you learn, explore, and innovate. Just like I'm doing right now! And with that, until next time, DannyDevs is out!
