<script setup>
// import associated .md files
import Lab007 from '../../components/content/lab007.md'

const { x, y } = useWindowScroll()

const { isSupported, open, sRGBHex } = useEyeDropper()
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab007: vueUse's useEyeDropper and the slick EyeDropper web API
      </h2>
      <p text-center>
        July 31, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div v-if="isSupported" text-center>
        <div mb-4>
          Your web browser supports the Eyedropper API: <span font-semibold>{{ isSupported }}</span>
        </div>
        <div mb-4>
          <p mb-4>Click the "Open Eyedropper" button and select any pixel on your monitor screen.</p>

          <p >sRGBHex color: {{ sRGBHex.toUpperCase() }}</p>
        </div>
        <div mb-6 mx-auto class="w-[100px] h-[100px]" :style="{ backgroundColor: sRGBHex }" />
        <button
          rounded-lg
          mb-10
          bg-red-500
          px-6 shadow-md text-white
          py-2

          :disabled="!isSupported"
          @click="open"
        >
          Open Eyedropper
        </button>
      </div>
      <div v-else>
        The Eyedropper API is not supported by your browser
      </div>
    </div>
    <!-- lab demo -->

    <Lab007 container/>

    <!-- spacer for mobile footer -->
    <div py-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
