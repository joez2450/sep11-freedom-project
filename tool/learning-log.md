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
Note: To apply attributes that edit text, there must be a comma and another bracket inside of the already existing parenthesis of `text()`. There must also be an ending bracket.

* Another feature I tested was adding shapes and adjusting its properties (particularly size)
    * I looked through the shapes section of the documentation under "components" and looked through the existing examples given
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

* The last feature I focused on was sprites
    * I imported a template from Kaboom called "mygame" and downloaded an image and then uploaded it to the sprite folder. Subsequently, I used this code to load the sprite:

``` JS
k.loadSprite("smiley", "sprites/smileyOne.jpg")

add([
    sprite("smiley"),
])

```

Note: The first quotation marks in the `loadSprite` parenthesis is the name you desire the image to be. The second quotation is to get the file path for the image to display it.

Note #2: A sprite is generally an image or animation that is used in a game

* Next Steps: Watch youtube videos to guide me through the tool's features and continue to focus on sprites properties and start movement mechanics

### 10/21/24
* I watched a [youtube video](https://www.youtube.com/watch?v=WevIqoWS2L8&list=PLu9YVdNl8Gec9Tn_YWS9XMEy7UCdOi-FQ&index=3) and followed through a Kaboom [intro documentation](https://kaboomjs.com/doc/intro)
* I added a new platform and set a gravity along with a body component so that my existing sprites would fall down.
    * I made the platform static so the sprites cannot go through to the void. The code to all of these actions was:

``` Js
k.setGravity(2400)
const bean = add([
    sprite("bean"),
    pos(50, 30),
    area(),
    body(),
])

add([
    rect(width(), 70),
    pos(0, height() - 100),
    outline(4),
    area(),
    body({ isStatic: true }),
    color(127, 200, 255),
])
```
NOTE: Static means to stay in place. It is not dynamic - or changing. The `area` component adds a collider to a sprite so when it hits something, there will be a collision.

* Next, I added a feature where sprites could jump. I imported a set of code from Kaboom to make it where when once one button is held down, my sprite would jump. The code to all of this was:

```Js

onKeyPress("space", () => {
    if (bean.isGrounded()) {
        bean.jump();
    }
});
```
Note: If the `if` statement with `bean.isGrounded` was removed from the set of code, a sprite can jump infinitely in the air without any barriers like Flappy Bird. The statement restricts it to where the sprite can only jump when it is on the ground.

* I added obstacles on the platform subsequently. I used the rectangle component and set a certain dimension of (40, 50) to make jumps possible.
    * I used the `pos` component and set it to a height of `height() - 100` to position the rectangle to an angle in the air. I also used the static feature to make the shape an unpassable object.
        * I added a loop so there was a continous amount of obstacles that appeared.
``` Js

loop(1, () => {
add([
    rect(40, 50),
    area(),
    pos(width(), height() - 100),
    anchor("botleft"),
    color(255, 180, 255),
    body({ isStatic: true }),
    move(LEFT, 1000),
]);
});

```
Note: The `move` component allows your screen to move in a direction infinitely. In the example, the sprite is always moving to the left side because it is given the value of `LEFT`. The number besides the direction indicates the movement of pixel per second, so the higher the value, the faster a sprite goes.

Note #2: The `color` component uses RGB values. Additionally the number besides the loop indicates how many seconds it would take for another obstacle to appear.

* At last, I followed the tutorial to make my sprite shake whenever it hits an obstacle. I used the `.oncollide` and `.shake` component as shown on the documentation and used a keyword to put onto my sprite in order for the effect to work. The code looked like this:


```Js

bean.onCollide("happy", () => {
    addKaboom(bean.pos);
    shake();
});

```

Note: The "happy" inside the parenthesis is a keytag that allows the obstacle to make the sprite shake once it collides. If a obstacle doesn't contain the tag, then there will be no shake effect.

Next Steps: Continue to explore the intro document and learn new components


### 11/3/24
* My first step was to look back into the [intro document](https://kaboomjs.com/doc/intro) from last time
 * This week, I wanted to make a score counter and game over screen for the intro game that I previously worked on. These were my two main objectives. I also wanted to learn any additional components that can be implemented for my future game.
* As for creating the score counter, I followed the tutorial and created a new variable with the value of `add` game objective and the components of `text` and `pos` within it. I readjusted the position to match the game while adding "Score" within the `text` parenthesis. Additionally, I created a variable `score` and set it to the value of 0. In the end, my code looked like this:

``` Js
let score = 0;

    const scoreLabel = add([
        text(score),
        pos(24, 24),
    ]);

```
* After creating a score tracker, I created a new function that would update the numbers by every frame. In the tutorial, it recommended that I used increments (`++`) from JavaScript and set `scoreLabel` to `score`. I followed the steps and created a system that actively updates a user's score when playing the game. The results looked like this:

```Js
 onUpdate(() => {
        score++;
        scoreLabel.text = score;
    });
```

Note: This system makes it where the value of `scoreLabel.text` increases by one in a frame per second, or in other words, depending on FPS, your score will go up drastically.

* Additionally, I learned the `wait(rand(number, number), functionName)` component. I used it as an alternative from using loops to generate more obstacles at a interval:

``` Js
wait(rand(1, 2), spawnTree);
```

Note: For every 1-2 seconds, a function with whatever shape conditions inside will occur. Therefore, an unlimited amount of obstacles can solely be generated through this code. The `wait` is depended on `rand(1,2)`, which then takes effect of the function.

* I used a `scene` component syntax and included a key tag of "lose". Inside `scene`, I used the `add` component and included a `text` of "Game Over!". Additionally, I created another `scene` with a key tag of "start" and used `add` to input a sprite. Afterward, I utilized a new component `go` with "start" along with `onClick` so that when a user loses they could respawn with a click. In the end, the code looked like this:

``` Js

scene("start", () => {
    add([
        sprite("bean"),
    ])
})

scene("lose", () => {
    add([
        text("Game Over"),
    ])
})

  onClick(() => go("game"));
```

Next Steps: Try to make a simple game of my own and continue to watch tutorials to learn new components
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
