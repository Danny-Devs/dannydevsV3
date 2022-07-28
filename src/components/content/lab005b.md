The author also made a [pinball machine](https://lonekorean.github.io/javascript-physics/demos/pinball/index.html) that was quite fun to play around with and analyse. It does lack realism when it comes to the levers--the lever should exert the greatest force on the ball when the ball is closer to the end of the lever, but in the simulation, the lever provides the greatest force when the ball is in the middle area. Still, it's a super cool demo of what a more involved project can feel like with the power of matter.js.

## Summary

It was quite interesting to integrate matter.js into my website. I'm finding that since my labs are so wide-ranging, I will have to eventually install more and more packages, which means more and more weight/bloat/decreased performance. We'll see as I go along; my most recent Google Lighthouse scores were all in the 90s, which was great to see. Vitesse and Vue are doing their job well!

Besides minding website weight, I also had to utilize Vue's template ref pattern of connecting to the DOM. Not only is this best practice when needing to connect directly to the DOM, but I couldn't get things working with matter until I changed the sample code I was using from vanilla JS dom manipulation to Vue template refs.

Lastly, because I used the template refs, I had to move nearly all my matter code into an onMounted hook, because otherwise matter would try to connect to the DOM with a null template ref. It wasn't so bad, but I did have to move my matter engine creation code (just a couple lines) outside of onMount so that I could access the engines (I had two of them in the same file, one for each demo) from the "root" scope, which I had to do with an event callback that needed to be accessible from the template, not nested in onMount.

The last part of the bead-dropping tutorial involves detecting collision and changing peg color from green to blue. This showed me a bit about how matter's event system works. My next steps will be to add more interactivity to matter simulations/experiences. See you then! Dannydevs out.
