<script setup>

</script>

<template>
  <main sm:px-12 lg:px-24 xl:px-96 dark:bg-gray-900 bg-cyan-400 flex justify-between items-center>
    <div pl-2 pt-7 pb-4>
      <img v-if="!isDark" w-48 src="/dannydevs-logo.png" alt="DannyDevs logo">
      <img v-if="isDark" w-48 src="/dannydevs-logo-cyan.png" alt="DannyDevs logo">
    </div>

    <div sm:flex sm:mt-3>
      <!-- navigation links for sm: and up -->
      <section hidden sm:block dark:text-cyan-400>
        <div class="flex">
          <router-link
            to="/"
            flex

            items-center
          >
            <p text-lg mr-6>
              Home
            </p>
          </router-link>
          <router-link to="/lab" flex items-center>
            <p text-lg mr-6>
              Lab
            </p>
          </router-link>
          <router-link to="/blog" flex items-center>
            <p text-lg mr-6>
              Blog
            </p>
          </router-link>
          <router-link to="/about" flex items-center>
            <p text-lg mr-6>
              About
            </p>
          </router-link>
        </div>
      </section>
      <!-- end navigation links for sm: and up -->

      <div @click="toggleDark()">
        <div
          v-if="!isDark"
          mr-2
          text-2xl
          i-carbon-moon
        />
        <div
          v-if="isDark"
          mr-2
          text-2xl
          i-carbon-sun
          text-cyan-400
        />
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>
