<script setup>
const props = defineProps({
  title: {
    type: String,
    default: '',
  },
  content: {
    type: String,
    required: true,
  },
  hasButton1: {
    type: Boolean,
    default: false,
  },
  button1Text: {
    type: String,
    default: '',
  },
  hasButton2: {
    type: Boolean,
    default: false,
  },
  button2Text: {
    type: String,
    default: '',
  },
  textCenter: {
    type: Boolean,
    default: true,
  },
  textLeft: {
    type: Boolean,
    default: false,
  },

})

const emit = defineEmits(['closeModal'])

const modalCard = ref(null)

onClickOutside(modalCard, () => {
  emit('closeModal')
})
</script>

<template>
  <div fixed top-0 bottom-0 left-0 right-0 flex justify-center class="bg-[#555555da]">
    <div ref="modalCard" text-center dark:bg-slate-900 bg-white class="h-min w-[90%] sm:w-[75%] mt-[50%] sm:mt-[10%]" px-4 pt-4 pb-10>
      <div flex justify-end>
        <div hover:cursor-pointer i-carbon-close @click="$emit('closeModal')" />
      </div>
      <h6 mb-4>
        {{ title }}
      </h6>
      <p mb-8 px-8 :class="{ 'text-center': textCenter, 'text-left': textLeft }">
        {{ content }}
      </p>
      <div flex gap-4 justify-center>
        <button v-if="hasButton1" border-violet-600 border-2 hover:bg-violet-600 dark:border-violet-500 dark:text-violet-400 text-violet-600 hover:text-white px-6 pt-2 pb-1 rounded-lg>
          {{ button1Text }}
        </button>
        <button v-if="hasButton2" dark:border-violet-500 border-violet-600 border-2 hover:bg-violet-600 text-violet-600 dark:text-violet-400 hover:text-white px-6 pt-2 pb-1 rounded-lg>
          {{ button2Text }}
        </button>
      </div>
      <div />
    </div>
  </div>
</template>
