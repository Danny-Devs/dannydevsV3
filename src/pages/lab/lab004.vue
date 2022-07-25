<script setup>
import Lab004 from '../../components/content/lab004.md'
import Lab004b from '../../components/content/lab004b.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})

const handleScroll = () => {
  window.scroll({
    top: 500,
    behavior: 'smooth',
  })
}

const handleWheel = (evt) => {
  evt.preventDefault()
  evt.currentTarget.scrollLeft += evt.deltaY
}
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab004: Unwrapping the Scrolling Web APIs
      </h2>
      <p text-center>
        July 25, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- copy -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <p text-left mb-4>
        My interest in the scrolling web APIs was piqued by a Stack Overflow <a target="_blank" href="https://stackoverflow.com/questions/73098530/vue-horizontal-scrolling">question</a> about how to scroll horizontally through icons with a mouse wheel. This question popped the lid open on a chest full of related questions that I had been meaning to find the answers to. On this website, for instance, I ran into issues trying to create a footer that would either be visible in an absolute position at the bottom if the page content was smaller than 100vh, or would come into view when the page content was larger than 100vh and the user scrolled down to the end of the page.
      </p>
      <p text-left mb-8>
        I would also like to learn how to animate on scroll, whether it's parallax or non-parallax animation; how to build an infinite scroll experience; and even just simply how to scroll (rather than jump) to a specific element.
      </p>

      <div text-center justify-around>
        <button
          class="dark:hover:bg-indigo-600"
          shadow-lg
          transition
          hover:scale-105
          dark:text-white
          active:bg-amber-300
          active:shadow-none
          bg-amber-400
          dark:bg-indigo-700
          py-3
          px-6
          rounded-lg
          text-xl
          @click="handleScroll"
        >
          click to scroll
        </button>
      </div>
    </div>
    <!-- end copy -->

    <lab004 />

    <div
      bg-slate-300
      dark:bg-slate-500
      flex
      gap-4
      overflow-auto
      px-4
      py-6
      w-full
      @wheel="handleWheel($event)"
    >
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Lorem ipsum, dolor sit amet consectetur elit.
      </div>
      <div bg-violet-400 shadow-md rounded-md dark:text-white dark:bg-violet-800 p-2>
        Sed ut perspiciatis unde omnis iste natus error.
      </div>
      <div bg-indigo-400 shadow-md rounded-md dark:text-white dark:bg-indigo-800 p-2>
        Lorem ipsum, dolor sit amet consectetur elit.
      </div>
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Quis autem vel eum iure reprehenderit qui.
      </div>
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Sed ut perspiciatis unde omnis iste natus error.
      </div>
      <div bg-violet-400 shadow-md rounded-md dark:text-white dark:bg-violet-800 p-2>
        Quis autem vel eum iure reprehenderit qui.
      </div>
      <div bg-indigo-400 shadow-md rounded-md dark:text-white dark:bg-indigo-800 p-2>
        Lorem ipsum, dolor sit amet consectetur elit.
      </div>
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Sed ut perspiciatis unde omnis iste natus error.
      </div>
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Quis autem vel eum iure reprehenderit qui.
      </div>
      <div bg-violet-400 shadow-md rounded-md dark:text-white dark:bg-violet-800 p-2>
        Lorem ipsum, dolor sit amet consectetur elit.
      </div>
      <div bg-indigo-400 shadow-md rounded-md dark:text-white dark:bg-indigo-800 p-2>
        Sed ut perspiciatis unde omnis iste natus error.
      </div>
      <div bg-purple-400 shadow-md rounded-md dark:text-white dark:bg-purple-800 p-2>
        Lorem ipsum, dolor sit amet consectetur elit.
      </div>
      <div bg-violet-400 shadow-md rounded-md dark:text-white dark:bg-violet-800 p-2>
        Quis autem vel eum iure reprehenderit qui.
      </div>
    </div>

    <Lab004b />

    <div my-12 />
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
