<script setup>
const isAVisible = ref('false')
const isExp = ref('false')

const toggleAnimationA = () => {
  isAVisible.value = !isAVisible.value
}
const toggleExp = () => {
  isExp.value = !isExp.value
}
</script>

<template>
  <div container px-4 sm:px-8 lg:px-36 mx-auto h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex justify-between items-center>
      <h2 text-3xl>
        lab001: Animation and Vue
      </h2>
      <p>July 18, 2022</p>
    </div>
    <hr>
    <!-- end header -->

    <!-- copy -->
    <div mx-4 mt-10>
      <p text-left mb-8>
        The animations below were made using Vue's built-in <a hover:cursor-pointer font-bold href="https://vuejs.org/guide/built-ins/transition.html" target="_blank">Transition component</a> and regular old CSS! The Transition component is a utility animation "wrapper" component that wraps the markup whose state we want to animate. It wires things up to allow us to start animating in CSS right away.
      </p>
    </div>
    <!-- end copy -->

    <!-- section fade-in -->
    <div>
      <p text-center py-2 class="w-1/2 md:w-1/3 mx-auto" border-b-1 text-xl mb-2>
        Fade-in/Fade-out
      </p>

      <div text-center>
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
          mt-8
          @click="toggleAnimationA"
        >
          trigger animation
        </button>
      </div>

      <div h-60 sm:h-36 grid grid-cols-1 sm:grid-cols-2 gap-4 my-8 md:px-8 lg:px-12 xl:px-36>
        <Transition name="fade">
          <p v-if="!isAVisible" text-xl text-left mx-auto mt-4>
            This piece of markup fades in and out in half a second, using Transition and the CSS opacity property.
          </p>
        </Transition>
        <p v-if="!isAVisible" text-xl text-left mx-auto mt-6>
          This piece of markup has no animation on it. This is what transitions look like out of the box. Which do you like better?
        </p>
      </div>
    </div>
    <!-- end section fade-in -->
    <hr my-12>
    <!-- section experiments -->
    <div>
      <p text-center py-2 class=" w-5/8 md:w-1/2 mx-auto" border-b-1 text-xl mb-2>
        Experimenting with CSS animation
      </p>

      <div text-center>
        <button
          class="dark:hover:bg-indigo-600"
          dark:bg-indigo-700
          dark:text-white
          shadow-lg
          transition
          hover:scale-105
          active:bg-amber-300
          active:shadow-none
          hover:bg-amber-300
          bg-amber-400
          py-3
          px-6
          rounded-lg
          text-xl
          mt-8
          @click="toggleExp"
        >
          trigger animation
        </button>
      </div>

      <div h-24 flex justify-center mt-7>
        <Transition name="slide">
          <p v-if="!isExp" text-6xl sm:text-7xl mt-6>
            Hello&nbsp;
          </p>
        </Transition>
        <Transition name="rotate">
          <p v-if="!isExp" text-6xl sm:text-7xl mt-6>
            World!
          </p>
        </Transition>
      </div>

      <div mx-4 md:mx-16 lg:mx-64>
        <p mt-4 px-4>
          You can create your own custom animations using using <a font-semibold href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions" target="_blank">CSS transitions</a> as well as <a font-semibold href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations" target="_blank">CSS keyframe animations</a>.
        </p>
        <p mt-4 px-4 pb-32>
          I'll be doing some experimentation with GSAP (Greensock animation) next, which allows for more animation control, power, and DX (developer experience)! Until next time, DannyDevs out!
        </p>
      </div>
    </div>
    <!-- end section experiments -->
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.slide-enter-active {
  animation-duration: 1s;
  animation-name: slidein;

}
.slide-leave-active {
  transition: opacity 0.5s ease;

}
@keyframes slidein {
from {
    transform: translateX(-100%);
  }

  to {
    transform: translateX(0);
  }
}
.slide-enter-from {

}

.slide-leave-to {
  opacity: 0;
  animation-duration: 0.5s;
  animation-name: slideout;
}
@keyframes slideout {
from {
    transform: translateY(0%);
  }

  to {
    transform: translateY(-300%);
  }
}
.rotate-enter-active {
  animation-duration: 1s;
  animation-name: rotator;
}

.rotate-leave-active {
  transition-property: opacity, background-color;
  transition-duration: 0.6s;
}

@keyframes rotator {
  0% {
    transform: rotate(0deg)
  }
  20% {
        transform: rotate(15deg)

  }
  40% {
        transform: rotate(-15deg)

  }
  60% {
        transform: rotate(5deg)

  }
  80% {
        transform: rotate(-5deg)

  }
  100% {
        transform: rotate(0deg)

  }
}

.rotate-enter-from {
  transform: rotate(0deg);
}

.rotate-leave-to {
  opacity: 0;
  background-color: cyan;
}
</style>

<route lang="yaml">
meta:
  layout: home
</route>
