<script setup>
import Lab003 from '../../components/content/lab003.md'
const question = ref('')
const answer = ref('')

watch(question, async (newQuestion, oldQuestion) => {
  if (!newQuestion) {
    answer.value = ''
    return
  }
  if (newQuestion.includes('?')) {
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    }
    catch (error) {

    }
  }
})

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab003: Having fun with a Random Yes/No free API
      </h2>
      <p text-center>
        July 23, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->
    <div text-center mt-6>
      <p text-xl>
        Ask a yes/no question:
      </p>
      <p text-xl>
        <em>hint: questions end with a '?'!</em>
      </p>
      <input v-model="question" mt-3 px-5 py-3 class="w-5/6 xl:w-1/2 border-2 border-red-400 rounded-lg" type="text">

      <p mt-8 text-xl>
        The answer is:
      </p>
      <p text-5xl mt-2>
        {{ answer }}
      </p>
    </div>
    <!-- content -->
    <hr mt-10>

    <Lab003 pb-24 />

    <!-- <a href="https://vuejs.org/guide/essentials/watchers.html" target="_blank">Vue documentation on Form Input Bindings</a> -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
