<script setup>
// import associated .md files
import Lab009 from '../../components/content/lab009.md'

const { x, y } = useWindowScroll()
onMounted(() => {
  x.value = 0
  y.value = 0
})

// watchEffect(() => {
//   if (input.value) {
//     input.value.focus()
//   } else {
//     // not mounted yet, or the element was unmounted e.g. by v-if
//   }
// })
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab009: Tip Calculator
      </h2>
      <p text-center>
        Aug 3, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div rounded-lg bg-white grid grid-cols-1 sm:grid-cols-2 gap-4 pb-6>
        <!-- column 1 -->
        <div bg-white rounded-lg px-6 pt-6 mb-4>
          <!-- block 1 -->
          <div>
            <p>Bill</p>
            <div rounded-md w-full class="bg-[#F3F9FA]" py-2 px-4 flex justify-between>
              <p>$</p>
              <p>142.55</p>
            </div>
          </div>
          <!-- block 2 -->
          <div>
            <p>Select Tip %</p>
            <div grid grid-cols-2 sm:grid-cols-3 gap-x-3 gap-y-3>
              <div class="bg-[#00474B] rounded-md text-white" text-center py-3 text-xl font-semibold>
                5%
              </div>
              <div class="bg-[#00474B] rounded-md text-white" text-center py-3 text-xl font-semibold>
                10%
              </div>
              <div class="bg-[#26C2AE] rounded-md text-white" text-center py-3 text-xl font-semibold>
                15%
              </div>
              <div class="bg-[#00474B] rounded-md text-white" text-center py-3 text-xl font-semibold>
                25%
              </div>
              <div class="bg-[#00474B] rounded-md text-white" text-center py-3 text-xl font-semibold>
                50%
              </div>
              <div class="bg-[#F3F9FA] rounded-md text-[#547878]" text-center py-3 text-xl font-semibold>
                Custom
              </div>
            </div>
          </div>
          <!-- block 3 -->
          <div>
            <p>Number of People</p>
            <div rounded-md w-full class="bg-[#F3F9FA]" py-2 px-4 flex justify-between>
              <div i-carbon-user />
              <p>5</p>
            </div>
          </div>
        </div>

        <!-- column 2 -->
        <div rounded-lg class="bg-[#00474B]" mx-6 pt-10 sm:mt-6 pb-6 px-6 flex flex-col>
          <!-- row 1 -->
          <div flex gap-4 justify-between>
            <div text-left>
              <p text-white>
                Tip Amount
              </p>
              <p class="text-[#7F9D9F]">
                / person
              </p>
            </div>
            <div class="text-[#26C2AE]" text-3xl>
              $0.00
            </div>
          </div>
          <!-- row 2 -->
          <div flex gap-4 mt-8 justify-between>
            <div>
              <p text-white>
                Total
              </p>
              <p class="text-[#7F9D9F]">
                / person
              </p>
            </div>
            <div class="text-[#26C2AE]" text-3xl>
              $0.00
            </div>
          </div>
          <!-- row 3 -->
          <div text-center mt-8>
            <button class="bg-[#26C2AE]" py-3 block w-full font-bold rounded-md>
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

</style>

<route lang="yaml">
meta:
  layout: home
</route>
