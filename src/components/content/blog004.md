
# Managing Different Screen Sizes with Responsive Design

Currently, mobile devices account for more web traffic (50.48%) than desktop devices (45.51%) followed by tablets (3%). So, approximately half of web traffic is mobile, and half is desktop, with a small percentage from tablets.

Prior to the explosion of mobile phones, nearly all web traffic was from desktop devices. There was no such thing as mobile-responsive design. Yes, screens varied in resolution, but mobile phones have not only a major difference in size, but also a radical difference in proportion, being vertical.

Here are the dimensions of various mobile phones, taken from Google Chrome's Dev Tools (responsive view mode, 2nd button from upper left corner:

- iPhone SE: 375 x 667
- iPhone 12 Pro: 390 x 844
- Google Pixel 5: 393 851
- Samsung S8+: 360 x 740
- Samsung Galaxy S20 Ultra: 412 x 915

Here are the dimensions of some tablets (vertical followed by horizontal):

- iPad Air: 820 x 1180, or 1180 x 820
- iPad Mini: 768 x 1024, or 1025 x 768
- Surface Pro 7: 912 x 1368, or 1368 x 912

from [ios-resolution.com](https://www.ios-resolution.com/)

- iPad Mini (6th gen): 744 x 1133
- iPad (9th gen): 810 x 1080
- iPad Pro (5th gen 12.9"): 1024 x 1366
- iPad Pro (5th gen 11"): 834 x 1194
- iPad Air (4th gen): 820 x 1280

Here are the most popular desktop screen resolutions, according to
[statcounter](https://gs.statcounter.com/screen-resolution-stats/desktop/worldwide):

- 1920 x 1080 (HD): 22.96%
- 1366 x 768: 17.89%
- 1536 x 864: 11.35%
- 1280 x 720: 6.19%
- 1440 x 900: 5.85%
- 1600 x 900: 3.57%
- 2560 x 1440 (QHD): ~2%

Check out [this](https://www.designrush.com/agency/web-development-companies/trends/website-dimensions#:~:text=5%20Most%20Common%20Desktop%20Screen%20Resolutions%20Worldwide,-According%20to%20StatCounter&text=1366x768%20\(22.98%25\),1536x864%20\(7.92%25\)) article if you want to peruse some more statistics.

## Analysis

At the simplest, I as a responsive designer would design for:

- 360 x 600, which should cover mobile sizes nicely
- 1920 x 1080 to cover the largest desktop category
- desktop width down to 1280px to cover rest of smaller resolution desktops
- test on desktop ultrawide on my own ultrawide monitor
- for tablets I would test down at 740 width, which is the boundary for smallest resolution, up to 1024 width. We don't care too much about height (vertical vs horizontal orientation) because users are so comfortable scrolling--it's width that is usually more important for responsive design.

I have been using Tailwind's default responsive design breakpoint [system](https://tailwindcss.com/docs/responsive-design) to make my websites responsive. There are five default breakpoints, inspired by common device resolutions:

| Breakpoint prefix  | minimum width | CSS |
| ----------- | ----------- | ----------- |
| `sm` | 640px | `@media (min-width: 640px) { ... }` |
| `md` | 768px | `@media (min-width: 768px) { ... }` |
| `lg` | 1024px | `@media (min-width: 1024px) { ... }` |
| `xl` | 1280px | `@media (min-width: 1280px) { ... }` |
| `2xl` | 1536px | `@media (min-width: 1536px) { ... }` |

Sample code would look like this:

```html
  <div class="mx-4 sm:mx-8">
    <!-- content -->
  </div>
```

The `mx-4` class shorthand indicates a margin of 4 on the x-, or horizontal, axis, which means a margin-left and margin-right of 1rem. Tailwind users must frequently consult the docs until they memorize how to do what they want; here is the [docs](https://tailwindcss.com/docs/margin) page for the margin utilities.

Normally, the `mx-4` class would apply to all breakpoint sizes, but notice the `sm:mx-8` to the right. The `sm:` designates that at the small breakpoint, which is at 640px, it's rule will take over any other `mx` rule below it in size.

If there are no rules specified for `mx` at larger breakpoints, the rule of the largest breakpoint will cascade up to any larger breakpoints.

If there are no breakpoints specified, the rule will never change regardless of web page width.

Of course we can specify widths of the larger breakpoints, which would look something like:

```html
  <div class="px-4 sm:px-8 md:px-12 lg:px-16 xl:px-24 2xl:px-36">
    <!-- content -->
  </div>
```

Now I specified unique padding on the x-axis (i.e. padding-left and padding-right) for every single breakpoint. As the width of the browser page changes, the padding adjusts often.

Learning to design websites and web apps responsively can be a daunting task due to the sheer number and diversity of screen sizes. However, the tooling for responsive design makes doing so easier, whether you are using Tailwind's abstracted approach, vanilla CSS media queries, or vueUse's [useMediaQuery](https://vueuse.org/core/usemediaquery/) composable to access CSS media queries in Javascript.

## Conclusion

When designing responsively, one of the first questions you want to answer is, "What resolution(s) will my users primarily be using?". If desktop, then I would go the desktop-first route while also ensuring the site reads well on mobile. If mobile, then I would go mobile-first while also keeping an eye on how things look at desktop (and less importantly, tablet--unless tablet is important to your project!).

What I would also recommend is that you either have some sort of design mock-ups (e.g. Figma files) that do the work of envisioning how the web app should look at different sizes, or think about the transitions and write and sketch out what you're envisioning if you don't have a design resource refer to. What you **don't** want to do is not plan ahead, because it's usually less efficient to not have a clear direction and strategy.

And with that, let's get to designing responsively with greater confidence and joy! I'm going to head over to [Frontend Mentor](https://www.frontendmentor.io/) to check out their HTML, CSS, and JS challenges. A pro subscription ($12/mo) allows access to Figma designs for each challenge, which will allow me to focus on development while also learning about designing in Figma. Till next time, DannyDevs out!
