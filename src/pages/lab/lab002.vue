<script setup>
import Lab002 from '~/components/content/lab002.md'

const { x, y } = useWindowScroll()
const isModalShowing = ref(false)

onMounted(() => {
  x.value = 0
  y.value = 0
})

const showModal = () => {
  isModalShowing.value = true
}
const closeModal = () => {
  isModalShowing.value = false
}
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab002: Modals in Vue
      </h2>
      <p text-center>
        July 22, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <p mt-8 text-center>
      Click on the button below to see a basic modal I created.
    </p>
    <div text-center pt-8 pb-8 sm:pb-16>
      <button shadow-lg bg-pink-400 dark:bg-transparent dark:border-2 class="dark:hover:bg-cyan-800" hover:bg-pink-300 px-8 py-3 rounded-3xl @click="showModal">
        show modal
      </button>
    </div>
    <Transition name="fade">
      <Modal
        v-if="isModalShowing"
        title="Your modal title goes here"
        content="What do you want to say? Let it all out here. This is the body content area of your brand new custom modal."
        has-button1
        button1-text="Your button #1"
        has-button2
        button2-text="Your button #2"
        @close-modal="closeModal"
      />
    </Transition>

    <Lab002 />
  </main>
</template>

<style scoped>
/* we will explain what these classes do next! */
.fade-enter-active {
  transition: opacity 0.2s ease;
}
.fade-leave-active {
  transition: opacity 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

<route lang="yaml">
meta:
  layout: home
</route>
