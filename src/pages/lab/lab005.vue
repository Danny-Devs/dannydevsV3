<script setup>
// import associated .md files
import Matter from 'matter-js'
import Lab005 from '../../components/content/lab005.md'
import Lab005b from '../../components/content/lab005b.md'

const { Bodies, Body, Composite, Engine, Events, Render, Runner } = Matter

const matterContainer = ref(null)
const matterContainer2 = ref(null)
const { x, y } = useWindowScroll()

// initialize Matter
// create engine
const engine = Engine.create()
const engine2 = Engine.create()

// wall creation
function wall(x, y, width, height) {
  return Bodies.rectangle(x, y, width, height, {
    isStatic: true,
    render: {
      fillStyle: '#868e96',
    },
  })
}

// peg creation
function peg(x, y) {
  return Bodies.circle(x, y, 14, {
    label: 'peg',
    restitution: 0.5,
    isStatic: true,
    render: {
      fillStyle: '#82c91e',
    },
  })
}

// bead creation
function bead() {
  return Bodies.circle(280, 40, 11, {
    restitution: 0.5,
    render: {
      fillStyle: '#e64980',
    },
  })
}

// button callback
function dropBead() {
  const droppedBead = bead()
  Body.setVelocity(droppedBead, { x: myRand(-0.05, 0.05), y: 0 })
  Body.setAngularVelocity(droppedBead, myRand(-0.05, 0.05))
  Composite.add(engine2.world, droppedBead)
}

// utility
function myRand(min, max) {
  return Math.random() * (max - min) + min
}

// this runs on mount
const runMatter = () => {
  // create renderer
  const render = Render.create({
    element: matterContainer.value,
    engine,
    options: {
      width: 250,
      height: 400,
      background: '#bef264',
      wireframes: false,
    },
  })
  const render2 = Render.create({
    element: matterContainer2.value,
    engine: engine2,
    options: {
      width: 560,
      height: 800,
      background: '#f8f9fa',
      wireframes: false,
    },
  })

  const boxA = Bodies.rectangle(200, 200, 20, 80, {
    render: {
      fillStyle: '#9333ea',
    },
  })

  const boxB = Bodies.rectangle(180, 50, 100, 30, {
    render: {
      fillStyle: '#fb923c',
    },
  })

  const ball1 = Bodies.circle(100, 100, 15, {
    render: {
      fillStyle: '#38bdf8',
    },
  })
  const ball2 = Bodies.circle(200, 0, 30, {
    render: {
      fillStyle: '#ef4444',
    },
  })
  const ground = Bodies.rectangle(125, 390, 250, 20, {
    isStatic: true,
    render: {
      fillStyle: '#ca8a04',
    },
  })
  const bottom = Bodies.rectangle(280, 800, 560, 20, {
    isStatic: true,
    render: {
      fillStyle: '#ca8a04',
    },
  })
  const leftLedge = Bodies.rectangle(50, 210, 100, 20, {
    isStatic: true,
    render: {
      fillStyle: '#ca8a04',
    },
  })

  // add dividers to the world
  for (let x = 80; x <= 560; x += 80) {
    const divider = wall(x, 610, 20, 360)
    Composite.add(engine2.world, divider)
  }

  // add field of pegs
  let isStaggerRow = false
  for (let y = 200; y <= 400; y += 40) {
    const startX = isStaggerRow ? 80 : 40
    for (let x = startX; x <= 520; x += 80)
      Composite.add(engine2.world, peg(x, y))
    isStaggerRow = !isStaggerRow
  }

  // add all of the bodies to the world
  Composite.add(engine.world, [boxA, boxB, ball1, ball2, leftLedge, ground])
  Composite.add(engine2.world, [bottom, wall(280, 0, 560, 20), wall(280, 800, 560, 20), wall(0, 400, 20, 800), wall(560, 400, 20, 800)])

  // run the renderer
  Render.run(render)
  Render.run(render2)
  // create runner
  const runner = Runner.create()

  // run the engine
  Runner.run(runner, engine)
  Runner.run(runner, engine2)

  function lightPeg(event) {
    event.pairs
      .filter(pair => pair.bodyA.label === 'peg')
      .forEach((pair) => {
        pair.bodyA.render.fillStyle = '#4c6ef5'
      })
  }

  Events.on(engine2, 'collisionStart', lightPeg)
}

onMounted(() => {
  x.value = 0
  y.value = 0
  runMatter()
})
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab005: A Very Important Matter(.js)
      </h2>
      <p text-center>
        July 27, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div flex flex-col items-center>
        <div ref="matterContainer" overflow-auto />
      </div>
    </div>
    <!-- lab demo -->

    <Lab005 container />

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div flex flex-col items-center>
        <button transition hover:bg-amber-300 active:translate-y-1 active:shadow-none bg-amber-400 shadow-lg mb-6 px-6 py-2 rounded-lg @click="dropBead">
          Drop bead
        </button>
        <div ref="matterContainer2" overflow-auto />
      </div>
    </div>
    <!-- lab demo -->

    <Lab005b />

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
