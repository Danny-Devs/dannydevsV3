<script setup>
// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components,
// they will be rendered correctly in the html results with vite-ssg
useHead({
  title: 'DannyDevs.com',
  meta: [
    {
      name: 'description',
      content: 'Website of DannyDevs, front end web developer, designer, and content creator',
    },
    {
      name: 'keywords',
      content: 'HTML, CSS, Javascript, Vue, VueJS, developer, Svelte, React, Solid, web developer, coder, coding, programming, computer, website, web app, designer, content creator, DannyDevs, Danny, DannyDevs.com',
    },
    {
      name: 'author',
      content: 'Daniel Ahn',
    },
    // {
    //   name: 'theme-color',
    //   content: computed(() => isDark.value ? '#00aba9' : '#ffffff'),
    // },
  ],
})
</script>

<template>
  <RouterView />
</template>
