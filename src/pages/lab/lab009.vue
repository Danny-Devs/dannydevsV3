<script setup>
// import associated .md files
import Lab009 from '../../components/content/lab009.md'

const { x, y } = useWindowScroll()
onMounted(() => {
  x.value = 0
  y.value = 0
})

const isCustomModalOpen = ref(false)

const bill = ref(null)
const numDiners = ref(1)
const percentTip = ref(null)
const customTip = ref(null)
const customTipInputEl = ref(null)
const billInputEl = ref(null)

watch(percentTip, () => {
  if (percentTip.value < 0)
    percentTip.value = 0
})

watch(numDiners, () => {
  if (numDiners.value < 1)
    numDiners.value = 1
})

watch(bill, () => {
  if (bill.value < 0)
    bill.value = null
})

watch(isCustomModalOpen, async () => {
  if (isCustomModalOpen.value) {
    await nextTick(() => {
      customTipInputEl.value.focus()
    })
  }
})

const totalBill = computed(() => {
  if (percentTip.value === 0)
    return bill.value
  if (percentTip.value > 0)
    return bill.value * (1 + percentTip.value / 100)
})

const totalTip = computed(() => {
  if (percentTip.value === 0)
    return 0
  if (percentTip.value > 0)
    return bill.value * (percentTip.value / 100)
})

const totalAmountPerPerson = computed(() => {
  if (bill.value && percentTip.value && numDiners.value) {
    if (totalBill.value)

      return (totalBill.value / numDiners.value).toFixed(2)

    else
      return null
  }
  return null
})

const tipAmountPerPerson = computed(() => {
  if (bill.value && percentTip.value && numDiners.value) {
    if (totalTip.value === 0)
      return 0

    else if (totalTip.value > 0)
      return (totalTip.value / numDiners.value).toFixed(2)
  }

  return null
})

const setPercentTip = (percent) => {
  percentTip.value = percent
}

const openCustomModal = () => {
// open modal with input for custom tip percentage
  isCustomModalOpen.value = true
}

const submitCustomTip = (event) => {
  // close modal
  isCustomModalOpen.value = false
  // set tip percentage
  percentTip.value = customTip.value
  customTip.value = null
}

const reset = () => {
  billInputEl.value.focus()
  bill.value = null
  numDiners.value = 1
  percentTip.value = null
}

</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab009: Tip Calculator
      </h2>
      <p text-center>
        Aug 6, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <!-- TIP CALCULATOR -->
      <div rounded-lg shadow-lg bg-white grid grid-cols-1 sm:grid-cols-2 gap-4 pb-6 class="font-space text-[#5E7A7D]">
        <!-- column 1 -->
        <div bg-white rounded-lg px-6 pt-6 mb-4>
          <!-- block 1 -->
          <div>
            <p mb-2 font-semibold sm:text-sm>
              Bill
            </p>
            <div mb-6 flex justify-between>
              <input ref="billInputEl" v-model="bill" relative text-right rounded-md w-full class="billInput bg-gray-200 focus:outline-2 focus:outline-[#26C2AE]" py-2 px-4 type="number" step="0.01" autofocus>
              <p
                absolute pl-2 pt-2 z-10 class="text-[#9EBBBD];"
              >
                $
              </p>
            </div>
          </div>
          <!-- block 2 -->
          <div mb-6>
            <p font-semibold sm:text-sm mb-3>
              Select Tip %
            </p>
            <div grid grid-cols-2 sm:grid-cols-3 gap-x-3 gap-y-3>
              <button class="bg-[#00474B] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-white" transition text-center py-3 sm:text-sm text-xl font-semibold @click="setPercentTip(5)">
                5%
              </button>
              <button class="bg-[#00474B] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-white" transition text-center py-3 sm:text-sm text-xl font-semibold @click="percentTip = 10">
                10%
              </button>
              <button class="bg-[#00474B] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-white" transition text-center py-3 sm:text-sm text-xl font-semibold @click="percentTip = 15">
                15%
              </button>
              <button class="bg-[#00474B] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-white" transition text-center py-3 sm:text-sm text-xl font-semibold @click="percentTip = 25">
                25%
              </button>
              <button class="bg-[#00474B] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-white" transition text-center py-3 sm:text-sm text-xl font-semibold @click="percentTip = 50">
                50%
              </button>
              <button class="bg-[#F3F9FA] active:bg-[#9FE8DF] hover:bg-[#26C2AE] rounded-md text-[#547878]" hover:bg-gray-200 text-center py-3 sm:text-sm text-xl transition font-semibold @click="openCustomModal">
                Custom
              </button>
              <Teleport to="body">
                <div v-if="isCustomModalOpen" aria-labelledby="modal-title" role="dialog" aria-modal="true">
                  <!--
                  Background backdrop, show/hide based on modal state.

                  Entering: "ease-out duration-300"
                    From: "opacity-0"
                    To: "opacity-100"
                  Leaving: "ease-in duration-200"
                    From: "opacity-100"
                    To: "opacity-0"
                -->
                  <div class="fixed inset-0 bg-gray-600 bg-opacity-75 transition-opacity" />

                  <div class="fixed z-10 inset-0 overflow-y-auto">
                    <div class="flex items-center justify-center min-h-full p-0">
                      <!--
        Modal panel, show/hide based on modal state.

        Entering: "ease-out duration-300"
          From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
          To: "opacity-100 translate-y-0 sm:scale-100"
        Leaving: "ease-in duration-200"
          From: "opacity-100 translate-y-0 sm:scale-100"
          To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
      -->
                      <div class="rounded-lg overflow-hidden shadow-xl transform transition-all sm:my-8 sm:max-w-lg sm:w-full">
                        <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                          <div class="mt-3 text-center sm:text-left">
                            <h3 class="text-lg text-gray-900">
                              Enter a custom tip %
                            </h3>
                            <div class="mt-2">
                              <input ref="customTipInputEl" v-model="customTip" text-right rounded-md w-full class="bg-[#F3F9FA] focus:outline-2 focus:outline-[#26C2AE]" py-2 px-4 type="number" step="1">
                            </div>
                          </div>
                        </div>
                        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                          <button class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm  px-4 py-2 bg-[#26C2AE] text-base font-medium text-white hover:bg-[#2fdac4] focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#26C2AE] sm:ml-3 sm:w-auto sm:text-sm" @click="submitCustomTip($event)">
                            Submit
                          </button>
                          <button type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm" @click="isCustomModalOpen = !isCustomModalOpen">
                            Cancel
                          </button>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </Teleport>
            </div>
          </div>
          <!-- block 3 -->
          <div>
            <p mb-2 font-semibold sm:text-sm>
              Number of People
            </p>
            <div mb-6 flex justify-between>
              <input v-model="numDiners" relative text-right rounded-md w-full class="dinerInput bg-gray-200 focus:outline-2 focus:outline-[#26C2AE]" py-2 px-4 type="number">
              <div
                absolute pl-2 pt-3 z-10 class="text-[#9EBBBD];"
              >
                <div i-carbon-user />
              </div>
            </div>
          </div>
        </div>

        <!-- column 2 -->
        <div rounded-lg class="bg-[#00474B]" mx-6 pt-10 sm:mt-6 pb-6 px-6 flex flex-col>
          <!-- row 1 -->
          <div flex gap-4 justify-between>
            <div text-left>
              <p text-white sm:text-sm>
                Tip Percent
              </p>
            </div>
            <div class="text-[#26C2AE]" text-3xl sm:text-2xl>
              {{ percentTip }}%
            </div>
          </div>
          <!-- row 1 -->
          <div flex gap-4 justify-between mt-6>
            <div text-left>
              <p text-white sm:text-sm>
                Tip Amount
              </p>
              <p sm:text-sm class="text-[#7F9D9F]">
                per person
              </p>
            </div>
            <div class="text-[#26C2AE]" text-3xl sm:text-2xl>
              ${{ tipAmountPerPerson }}
            </div>
          </div>
          <!-- row 2 -->
          <div flex gap-4 mt-6 justify-between>
            <div>
              <p sm:text-sm text-white>
                Total
              </p>
              <p sm:text-sm class="text-[#7F9D9F]">
                per person
              </p>
            </div>
            <div class="text-[#26C2AE]" text-3xl sm:text-2xl>
              ${{ totalAmountPerPerson }}
            </div>
          </div>
          <!-- row 3 -->
          <div text-center mt-8 flex h-full>
            <button self-end class="bg-[#26C2AE] hover:bg-[#2cd6c0] active:bg-[#9FE8DF] text-[#00474B]" py-3 block w-full font-bold rounded-md @click="reset">
              RESET
            </button>
          </div>
        </div>
      </div>
    </div>
    <!-- lab demo -->

    <Lab009 container />

    <!-- spacer for mobile footer -->
    <div py-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>
/* removes up/down arrows for number inputs */
/* Chrome, Safari, Edge, Opera */
.billInput::-webkit-outer-spin-button,
.billInput::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
.billInput {
  -moz-appearance: textfield;
}
</style>

<route lang="yaml">
meta:
  layout: home
</route>
