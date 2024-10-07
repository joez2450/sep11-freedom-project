# Tool Learning Log

## Tool: **Kaboom**

## Project: **Interactive Game**

---

### 9/30/24:
* I created a new directory and file to store my Kaboom progress
    * Next, I imported a CDN from [Kaboom.js tutorial documents](https://kaboomjs.com/doc/setup) to install all of the tool's feature
* Along with the first importation of code, I tested the text feature using this line of code syntax:

``` JS
kaboom();

add([
    text("I love to code!"),
    pos(120, 80),
]);
```
Note: `add` is classified as a game objective. It adds components into a game you desire. Therefore, all of these components must be added into an `add` bracket to appear. Everything after parenthesis also end with a comma.
Note #2:

* I learned that `pos` is used to position elements and `text` makes it possible to input a text into the screen
* The next feature I tested was `size`, `font`, and `width`
 * In the already existing `add` bracket, I added all three attributes underneath `pos`. The result looked like this:

 ``` JS
add([
    pos (250, 80),

        text ("I love to code!",{
        size: 76,
        width: 320,
        font: "sans-serif",
    }),
]);
 ```
NOTE: To apply attributes that edit text, there must be a comma and another bracket inside of the already existing parenthesis of `text()`. There must also be an ending bracket.

* Another feature I tested was adding shapes and adjusting its properties (particularly size)
    * I looked through the shapes section of the documentation under "components" and looked through the existing examples given.
        * The codes I imported from [Kaboom](https://kaboomjs.com/#polygon) and edited in the end were these:

 ``` JS
 add([
    pos(1400, 180),
    rect(100, 1000),
    outline(4),
    area(),
])

add([
    pos(1000, 180),
    circle(40),
])

 ```

* The parenthesis next to the `rect` has to values: width and height. Width comes before height in the syntax. As for the value inside the `circle` parenthesis, it represents the radius of the shape which has a direct correlation with size: the higher the radius, the bigger the circle.

* Next Steps: Watch youtube videos to guide me through the tool's features and focus on sprites
<!--

### X/X/XX:
* Text
>

<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
