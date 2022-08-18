<script setup>
import { useSound } from '@vueuse/sound'
import { useMyStore } from '~/store/myStore'
import shakeSfx from '/pill-shake.mp3'

const { play } = useSound(shakeSfx, {
  interrupt: true,
  volume: 0.1,
})

const isAnimating = ref(true)
const numMouseovers = ref(0)
const showDizzy = ref(false)
const nextDialog = ref(false)
const modalCard = ref(null)

// access global state
const myStore = useMyStore()

// set default scroll position
const { x, y } = useWindowScroll()

const triggerAnimation = () => {
  play()
  isAnimating.value = !isAnimating.value
  setTimeout(() => {
    isAnimating.value = !isAnimating.value
  }, 50)
  numMouseovers.value++
  if (numMouseovers.value > 2 && !myStore.hasPlayed) {
    showDizzy.value = true
    numMouseovers.value = -1000
  }
}

onMounted(() => {
  x.value = 0
  y.value = 0
  triggerAnimation()
})

const closeModal = () => {
  showDizzy.value = false
  myStore.hasPlayed = true
}

onClickOutside(modalCard, () => {
  showDizzy.value = false
})
</script>

<template>
  <main container mx-auto h-full>
    <!-- spacer -->
    <div py-5 />

    <!-- hero -->
    <div class="sm:(w-2/3 mx-auto) lg:w-1/2 xl:w-1/3" py-4 pl-12 dark:bg-slate-500 bg-red-500 flex items-center justify-center shadow-lg>
      <div>
        <img
          hover:cursor-pointer
          hover:scale-102
          transition
          :class="isAnimating ? 'animated-rotation' : ''"
          alt="DannyDevs avatar"
          src="/dannydevs-avatar.png"
          w-36
          sm:w-24
          @click="triggerAnimation"
        >
      </div>

      <!-- modal -->
      <Transition name="fade">
        <div v-if="showDizzy" absolute top-0 class="-bottom-96" right-0 left-0>
          <!-- modal background -->
          <div bg-gray-800 dark:opacity-93 opacity-60 w-full h-full />
          <!-- modal card -->

          <div ref="modalCard" bg-red-300 dark:bg-slate-600 absolute class="p-2 top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-96">
            <div hover:cursor-pointer i-carbon-close text-2xl mb-1 @click="showDizzy = false" />
            <div bg-red-50 dark:bg-slate-700>
              <div py-6 px-10>
                <slot name="body" />
                <p v-if="!nextDialog" text-lg>
                  Whoa, I'm getting real dizzy up in hizzy!!!
                </p>
                <p v-else-if="nextDialog" text-lg>
                  Those CSS animations are something, aren't they?
                </p>
              </div>
            </div>
            <div text-right>
              <button
                v-if="!nextDialog"
                bg-red-500
                dark:bg-cyan-600
                mt-2
                px-5
                py-2
                rounded-lg
                class="dark:hover:bg-cyan-500"
                hover:bg-red-400
                shadow-md
                active:shadow-none
                transition
                @click="nextDialog = true"
              >
                Next
              </button>
              <button
                v-if="nextDialog"
                bg-red-500
                class="dark:hover:bg-cyan-500"
                dark:bg-cyan-600
                hover:bg-red-400
                active:bg-red-500
                shadow-md
                active:shadow-none
                transition
                mt-2
                px-5
                py-2
                rounded-lg

                @click="closeModal"
              >
                Close
              </button>
              <slot name="footer" />
            </div>
          </div>
        </div>
      </Transition>

      <div ml-4 dark:text-black>
        <p sm:text-xl text-2xl text-center font-bold>
          Hi there!
        </p>
        <p sm:text-xl text-2xl text-center font-bold mr-6>
          Welcome to my
        </p>
        <p sm:text-xl text-2xl text-center font-bold mr-6>
          homepage.
        </p>
      </div>
    </div>
    <!-- end hero -->
    <br>

    <!-- main content -->
    <div text-lg px-4>
      <p dark:font-normal font-bold text-xl mb-6 text-center dark:text-cyan-300>
        My name is Danny, aka DannyDevs.
      </p>

      <div text-base class="sm:w-4/5 xl:w-2/3 mx-auto" dark:text-cyan-300 dark:bg-gray-900 mb-11 bg-red-50 px-6 py-6 rounded-lg>
        <p mb-4>
          I'm a front end web developer, designer, and content creator. I work primarily with Vue JS, but I've also worked with React and Svelte.
        </p>

        <p mb-4>
          You can find examples of my work in the <router-link font-bold underline to="/lab">
            <a>Lab</a>
          </router-link>.
        </p>

        <p mb-4>
          I write and educate about all things webdev in my <router-link font-bold underline to="/blog">
            <a>blog</a>
          </router-link>.
        </p>

        <p mb-4>
          Learn more about <router-link font-bold underline to="/about">
            <a>me</a>
          </router-link>. I'm available for employment opportunities!
        </p>
        <p>
          I also maintain a repository of useful web dev <router-link font-bold underline to="/links">
            <a>links</a>
          </router-link>.
        </p>
      </div>
      <!-- spacer for mobile footer -->
      <div py-8 />
      <!-- spacer for mobile footer -->
    </div>
    <!-- end main content -->
  </main>
</template>

<style scoped>
.animated-rotation {
  animation: rotation .2s linear;
  animation-iteration-count: 2;
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

.fade-enter-active
{
  transition: opacity .5s;
  opacity: 1;
}
.fade-leave-active {
  transition: opacity .5s;
  opacity: 1;
}

.fade-enter-from
{
  opacity: 0;
}
.fade-leave-to {
  opacity: 0;
}
</style>

<route lang="yaml">
meta:
  layout: home
</route>

