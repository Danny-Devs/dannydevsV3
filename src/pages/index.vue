<script setup>

</script>

<template>
  <main bg-red-50 dark:bg-slate-900>
    <div py-5 />

    <div class="sm:(w-1/2 mx-auto) xl:w-1/3" py-4 pl-12 dark:bg-slate-500 bg-red-500 flex items-center justify-center>
      <div>
        <img class="animated-rotation" w-36 src="/dannydevs-avatar.png" alt="DannyDevs avatar">
      </div>
      <div>
        <p text-2xl text-center font-bold>
          Hi there!
        </p>
        <p text-2xl text-center font-bold mr-6>
          Welcome to my homepage.
        </p>
      </div>
    </div>
    <br>

    <div text-lg px-4>
      <p dark:font-normal font-bold text-xl mb-6 text-center dark:text-cyan-300>
        My name is Danny, aka DannyDevs.
      </p>

      <div class="sm:w-2/3 xl:w-1/3 mx-auto" dark:text-cyan-300 dark:bg-gray-900 bg-white px-6 py-6 rounded-lg>
        <p mb-4>
          I'm a front end web developer, designer, and content creator who primarily works in Vue JS. I also admire Svelte.
        </p>

        <p mb-4>
          You can find examples of my work in the <router-link font-bold underline to="/lab">
            Lab
          </router-link>.
        </p>

        <p mb-4>
          I write and educate about all things webdev in my <router-link font-bold underline to="/blog">
            blog
          </router-link>.
        </p>

        <p>
          Learn more about <router-link font-bold underline to="/about">
            me
          </router-link>. I'm available for employment opportunities!
        </p>
      </div>
    </div>
  </main>
</template>

<style scoped>
.animated-rotation {
  animation: rotation .2s linear;
  /* animation-iteration-count: 1; */
}
@keyframes rotation {
  0% {
    transform: rotate(-5deg);
  }
  30% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(5deg);
  }
  80% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-5deg);
  }

}
</style>

<route lang="yaml">
meta:
  layout: home
</route>

