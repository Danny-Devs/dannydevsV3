The containing div's attributes include `overflow-auto`, which is Tailwind for adding the CSS property `overflow: auto`, which hides the overflow and provides a horizontal and/or vertical scrollbar as needed. The `@wheel="handleWheel($event)` listens for the mouse scroll wheel to move, then invokes a function and passes the event in as a parameter (the `$event` is provided by Vue because the code is in the template where we cannot easily get a reference to the event).

```html
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
```

`handleWheel` takes in the $event as a parameter, `evt`. We then call `preventDefault` on the event to prevent the mouse scroll wheel's default behavior: scrolling vertically. To ignore the items inside the containing div and only target the element that the event listener is attached to, we use `currentTarget` rather than `target`. We then convert the scroll wheel's default vertical scrolling into horizontal scrolling by accessing the `scrollLeft` property on the currentTarget, which controls the position of the horizontal scroll, and finally add or subtract the vertical change in position, `deltaY` to the currentTarget's `scrollLeft` property.

```js
const handleWheel = (evt) => {
  evt.preventDefault()
  evt.currentTarget.scrollLeft += evt.deltaY
}
```

## Discussion

In this lab, I learned that the scroll position (vertical and horizontal) can be controlled using `window.scroll`. The (x, y) coordinates of the scrolling web API are simple enough thanks to the resemblance to the Cartesian coordinate system. As a next step, I'd like to experiment with vueUse's [useScroll](https://vueuse.org/core/usescroll/#usescroll) utility, which provides reactive variables and convenient functions to enhance the web APIs.

Horizontal scrolling, which I thought would much more difficult to implement, was actually a breeze. I use Trello often, and Trello has a wonderful horizontally scrolling UI design; I find that the ability to organize things on a horizontal axis beyond the screen's boundaries is agreeably intuitive. A couple things Trello does that I'd like to explore is how it scrolls horizontally using the left/right wheel click, and how it scrolls horizontally when pressing "shift" and moving the mouse wheel "normally", i.e. rolling it forwards and backwards.

Super cool stuff! Onwards, friends! DannyDevs out...
