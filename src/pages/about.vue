<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main container mx-auto p-4 dark:text-cyan-300 min-h-screen>
    <div sm:px-12>
      <h1 text-center text-xl>
        bio
      </h1>
      <hr mb-4>
      <p>I grew up in Palos Verdes, a sheltered suburban coastal area of Los Angeles, California, since the age of seven</p>
      <br>
      <p>Since then I've had the good fortune to live in New York City for around five years. It's been illuminating to be able to compare and contrast two jewels of the East and West Coast of the United States.</p>
      <br>
      <p>Now, I am returning to my hometown of Los Angeles, and I'm excited to get reacquainted with the city and friends and family who live there.</p>

      <h1 text-center text-xl mt-6>
        interests
      </h1>
      <hr mb-4>

      <p>
        Ever since getting bitten by the coding bug, my interest in and appreciation for web development has grown. It has been an incredible journey navigating the front end and figuring out my place in web development. I explored everything from Dart and Flutter to Rust before deciding to focus on React due to its job market dominance.
      </p>
      <br>
      <p>However, after one too many pain points experienced in React world, I decided to give Vue another try. I came back at the perfect time, when the Vue development experience has never been better. Every day I get to expand my web-making capabilities with Vue 3, an elegant, modular, extensible, dependable, fast, light, and modern framework.</p>
      <br>
      <p>Nowadays my focus is on becoming a complete developer with facility in more advanced areas such as animation, forms and form validation, user auth, connecting to a backend, etc.</p>
      <br>
      <p>In my free time I enjoy exploring the Svelte JS framework as well as learning Three.js, D3.js, and other creative web arenas.</p>

      <h1 text-center text-xl mt-6 mb-2>
        skills
      </h1>
      <hr mb-4>
      <p>
        Vue
      </p>
      <p>Git/Github</p>
      <p>VS Code</p>
      <p>HTML, CSS, Javascript</p>
      <p>Photoshop, Illustrator</p>
      <p>Image Editing</p>
      <p>Illustration</p>
      <p>Svelte</p>

      <br>
      <p>Find out more at my <a underline target="_blank" href="https://www.linkedin.com/in/danielahn47/">LinkedIn page</a>.</p>
      <br>
      <br>
      <br>
      <br>
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
