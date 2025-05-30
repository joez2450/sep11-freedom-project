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


### 11/4/24
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

Note: For every 1-2 seconds, a function with whatever shape conditions (rectangles, triangles, circles) inside will be executed by the `rand` component. Therefore, an unlimited amount of obstacles can solely be generated through this code. The `wait` also depends on `rand(1,2)`, which then affects the function.

* I used a `scene` component syntax and included a key tag of "lose". Inside `scene`, I used the `add` component and included a `text` of "Game Over!". Additionally, I created another `scene` with a key tag of "start" and used `add` to input a sprite. Afterward, I utilized a new component `go` with "start" along with `onClick` so that when a user loses the game, they could respawn with a click. In the end, the code looked like this:

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

  onClick(() => go("start"));
```

Next Steps: To continue to review tutorials to learn new components and to build on the game


### 11/18/24
* This week, my main agenda was to continue to learn components that Kaboom has to offer and add more to the tutorial game
* I adjusted the position of my sprite using `center()` asset, so that it would spawn in the center of the screen instead of a specific (x,y) position
``` JS
const player = add([
        // list of components
        sprite("dino"),
        pos(center()),
        area(),
        body(),
    ]);
```
* Additionally, I swapped the default sprite to one that I desire. I gathered a new image and downloaded its file. I then uploaded it to GitHub, and transported into my repository.
 * I loaded the sprite using `loadsprite()` and changed the remaining codes with the tag "bean". I then used `scale()` and inserted a value of 0.7 within the parenthesis in order to lower the size of the sprite.

* A new component I learned was `onLoading` and the way to edit loading screens. On the Kaboom [playground tutorial](https://kaboomjs.com/play?example=loader), I went to see the syntax and reviewed each code. Then, in my IDE I created a `onLoading` event that included three other components:`drawRect`, `drawCircle`, and `drawText`. I added  respective attributes to each one of them.
    * I made the color of `drawRect` with a yellow RGB to have a colored background screen. I utilized `drawCircle` the same way from the website. Subsequently, `drawText` was used to display a "loading" text on the screen while the game assets were loading. I also used the same `repeat(wave(1, 4, time() * 12))` code, which was a mathematical operation. The code looked like this:

    ``` JS
  onLoading((progress) => {

        drawRect({
            width: width(),
            height: height(),
            color: rgb(182, 218, 14),
        })


        drawCircle({
            pos: center(),
            radius: 43,
            end: map(progress, 0, 1, 0, 360),
        })

        drawText({
            text: "loading" + ".".repeat(wave(1, 4, time() * 12)),
            font: "monospace",
            size: 36,
            pos: center().add(0, 70),
        })
    ```
* NOTE: The radius within `drawCircle` determines the size of the circle. The `repeat(wave(1, 4, time() * 12))` code is reponsible for the "..." animation next to the text "loading" by setting a timed interval in which the event would repeat.
* NOTE #2: In summary, the `onLoading` event loads a visual while all of the other assets are registering. This event tool can be useful especially for creating loading screens.

* I also utilized a `wait` component that would load a new sprite into a scene within a 3 second set interval. Visual of the code:

``` JS
    wait(3, () => {
        add([
            sprite("bean"),
            pos(291, 0),
            area(),
            body(),
        ]);

    })
```
NOTE: In 3 seconds, a the sprite "bean" would be spawned into the game scene. In order for the sprite to have the same effects as the original, there would need to be more code to modify its properties. The `wait` component is useful for adding sudden events in a game.

* Next Steps: Create a new file and incorporate various components that I have already learned into a scene, while also continuing to learn new concepts

### 12/2/24
* I browsed the Kaboom documentation page and focused on the concept of `addLevel` which is categorized under the level section.
  * I imported two new sprites to use as I wanted to create a separate level with blocks and spikes. In a new file, I added the same code from my previous game to build upon it.
* I used `loadsprite` to define my sprites into the Kaboom scene. Additionally, I used `addLevel`to build out a new scene using symbols. I used `^` to represent the spike sprite. As my second symbol, I used `>` to represent blocks. I utilized `@` to represent the player sprite. I then wrote out a line of code using the new component I learned to build a level layout:

``` JS
const LEVELS = [
    [
        "@  ^^  ^^    ^^ ^^  >",
        ">>>>>>>>>>>>>>>>>>>>>>>>>",
    ],
]

```
NOTE: The symbols represent the sprites and the location where they would be placed. The symbols in `addLevel` does not always need to contain sprites. It can include other features.
* Another step of using `addLevel` was to include properties of the symbol. I scaled down my spike and sprites using `scale` and also positioned them with `pos`. I also added a static body to the blocks so that the character sprite can land on it rather than fall through:

``` JS
tiles: {
            "@": () => [
                sprite("bean"),
                area(),
                body(),
                anchor("bot"),
                "bean",
            ],

            "^": () => [
                sprite("spike"),
                area(),
                anchor("bot"),
                scale(.2),

            ],
            ">": () => [
                sprite("block"),
                area(),
                anchor("bot"),
                scale(.01),
                pos(50, 350),
                body({ isStatic: true }),
                anchor("bot"),
            ],
        },

```
NOTE: All of the symbols can be given its own properties.

* At last, I added parameters into the scene so there would be a score counter. I used `scene("game", ({ levelIdx, score })`. I also created a new function so once a user spawns, the score would be initialized at zero:

```JS
function start() {
    go("game", {
        levelIdx: 0,
        score: 0,
    })
}
```

Next Steps: Continue to explore new components while also modifying my level and sprites

### 12/16/24
* My main goal for this week is to modify sprites and continue to the learn new components using the [Kaboom documentation](https://kaboomjs.com/).

* In the previous level I created, I continued to modify the user sprite which I added.
    * I used the `onKeyDown` component to set a keybind for the sprite to move left or right.
         * I created two distinct components and within the parenthesis added "left" and "right" to indicate the keybind needed in order for the conditions inside to register on the game scene. Inside both components, I added `bean.move` and included the values of `(-SPEED, 0)` for left and `(-SPEED, 0)` in the right one.

``` JS
onKeyDown("left", () => {
    bean.move(-SPEED, 0)
})


onKeyDown("right", () => {
    bean.move(SPEED, 0)
})

```

NOTE: Speed is a set variable with a value of 400. In the right `OnKeyDown`, the value of speed allows the user sprite to move to the right when the key is pressed down. In the left, speed has a negative sign in the front to initiate an inverse value that will allow the sprite to move to the left.

* Additionally, I imported a new sprite that represented a distinct block, which I named "bk" into the game scene. I gave the sprite the symbol ">" so that I could manage to place it in the level.

    * Then, I organized the level by rearranging the symbols accordingly to the way I envisioned. The code looked like this:


```
  [
        "@",
        ">   >   >  >  >  >   >   >   >   >   >",
    ],

```

NOTE: The `@` symbol represents the user sprite. The spaces in between the `>` creates a space between each block sprite.

* I modified the sprite's properties by applying ` body({ isStatic: true })` and ` scale(0.2)`.
* I tested out the `onUpdate` component on the user sprite. I included that if the user sprite's Y position was greater than or equal to 480, the scene will go back to a losing screen, which I created before. The code looked like this:

```JS
  bean.onUpdate(() => {
        if (bean.pos.y >= 480) {
            go("lose")
        }
    })
```

Next Steps: Connect my level to another one either through using `onUpdate` or a seperate component

### 1/6/25
* I connected a new level by adding onto the `LEVELS` variable I created previously that was within the game scene
    * I added new brackets and created new structures using the symbol >, which represented blocks:

    ``` JS
    [
        "@",
        "> > > > > > > >",
    ],
    ```
* I created a new portal sprite using `k.loadSprite` and gave it a new symbol so I can use it to transition into other levels. Additionally, I scaled the sprite down to 0.2 using `scale()` so that it would match the size of the other entities. I also used `pos()` to rearrange the location of the sprite portal.
    * Using the [documentation](https://kaboomjs.com/blog) on Kaboom as a reference, I create a new `Player.onCollide()` and added conditionals that would bring a user into a new level or a winning scene depending if they were on the last level or not (through variable comparisions) if it touched the portal sprite.

```JS
if (levelIdx < LEVELS.length - 1) {
			// Goes to next level if there is still one
			go("game", {
				levelIdx: levelIdx + 1,
				score: score,
			})
		} else {
			// Goes to win screen
			go("win", { score: score })
		}

```
NOTE: `levelIdx < LEVELS.length - 1` is an operation that checks the amount of levels within the `LEVEL` variable by the value of `levelIdx` which is the total amount of new platforms there are
in the game scene

* I also updated the score counter so that when a user passes one level, the number will increase. This was done inside the conditionals I made.
``` JS
if (levelIdx < LEVELS.length - 1) {
			// If there's a next level, load the next level in the same game scene
			go("game", {
				levelIdx: levelIdx + 1, // level counter
				score: score + 1, // increases the score by one
			})

```
* Additionally, I made sure that in every `go` component, the number was refreshed so the computer knew the defined score at all times.

Next Steps: Work on modifying the new level and create a new one after it


### 2/24/25

* I created two additional levels and modified them with sprites of appropriate sizes using symbols and brackets in my `LEVELS` variable.
    * I made it so that with each level, the difficulty increased.
``` JS
const LEVELS = [
[
		" @        /      /    	",
		"=====================  ",
		"						",
		"        			    ",
		"       >  ///   ///    /     ",
		"       ================= ",


	],
	[
		"  /              /   ",
		"  =              =   ",
		"   @    =            ",
		"   =        /  =      ",
		"     /      =      >  ",
		"     =             =  ",
	]
]
```

Reminder: A comma is used to indicate the end of a layer in a level. The closing bracket fully concludes the level. If there is another set of quotation marks present, a new layer is created in the same level.


* I added a new camera feature using two separate `camPos` enwrapped in `.onUpdate` and  a new component of `.onPhysicsResolve` so that it is always zoomed in onto the user sprite.

``` JS
player.onUpdate(() => {
		camPos(player.worldPos())
	})

	player.onPhysicsResolve(() => {
		camPos(player.worldPos())
	})
```

NOTE: `onPhysicsResolve` is more of an additional component that ensures a smooth movement tracking system when a user sprite lands onto the ground. `.onUpdate` alone would lock the camera position onto the user on every frame. These components also reduce the need to use media queries since it would be responsive for all device screen sizes.


* I also learned the `fixed` component on the documenetation. I used `fixed()`  on the score counter text in the `add` component to prevent it from exiting the screen when a user jumped in the obstacle courses.
    * I also used `pos` and set the value to (12,12) so that it would be perfectly in the top left of the screen.

``` JS
const scoreLabel = add([
		text(score),
		pos(12,12),
		fixed(),
	])
```
NOTE: The main function of `fixed()` is to make a component unaffected by the camera.

* I also used `setBackground(206, 242, 241)` to replace the default background and set it to a light blue color.

NOTE: `setBackground` uses RGB values. Additionally, you can also create a background by uploading a new sprite and putting it in `add`. But you also have to use transformation properties to cover the entire screen.

Next Steps: Add coins and more levels while also modifying them

### 3/3/25

* I created a pause method in my game using `onKeyPress`, conditional statements, and variations of the `pause` components.
    * This would allow a user to pause their game whenever they desired by pressing a specific key.

``` JS
let userPause = null
	onKeyPress("p", () => {
		game.paused = !game.paused
		if (userPause) userPause.cancel()
		userPause = tween(
			menu.pos,
			game.paused ? center() : center().add(0, 700),
			1,
			(p) => menu.pos = p,
			easings.easeOutElastic,
		)
		if (game.paused) {
			menu.hidden = false
			menu.paused = false
		} else {
			userPause.onEnd(() => {
				menu.hidden = true
				menu.paused = true
			})
		}
	})

    const menu = add([
		rect(300, 400),
		color(255, 0, 0),
		outline(2),
		anchor("center"),
		pos(center().add(0, 500)),
	])


```

NOTE: The variable userPause holds the animation that brings out the rectangle down by certain pixels when a user decides to press "p". The lower conditional statement makes it so that if a user pauses their game, `menu` would not be hidden and display the primitive on the screen. Otherwise if the pause time is ended, it makes it hidden.
NOTE #2: `game.paused = !game.paused` checks whether pause is active or not.

* Additionally, I tested out dynamic scaling methods on sprites using `onMouseMove` and dimensonal components such as `spr.width`, `spr.height`, `mousePos.x`, `mousePos.y`.
    * This allows a mouse to scale out sprites to any sizes being based on its position.
``` JS
const spr = add([
	sprite("spike"),
])

onMouseMove(() => {
	const mpos = mousePos()
	spr.width = mpos.x
	spr.height = mpos.y
})
```
NOTE: `.height` and `.width` will constantly change to match the (x,y) values on the coordinate plane, allowing it to grow smaller or bigger based on certain positions.

* I also tried out using `onMouseMove` and `addKaboom` by making it add a new sprite on the mouse position everytime it moves around.

``` JS
addKaboom(center())
onMouseMove(() => addKaboom(mousePos()))
```

NOTE: `addKaboom(center())` is a default sprite made by the developers. The center tag allows the sprite to be centered at a designated positon everytime it is being added.

Next Steps: Continue to learn more components, referring to the Kaboom documentation, and prepare to create new modifications in my game

### 3/17/25
* I created a start button in my game, which the user had to press before starting the interactive experience.
    * Inside a function hold three parameters one of which was text, I created the button itself using a variable and dimensional components within it. I then
      used the `add` component to the button variable to add a text based on the parameter input.
``` JS
function button(txt, p, f) {

    const btn = add([
		rect(240, 80, { radius: 8 }),
		pos(p),
		area(),
		scale(1),
		anchor("center"),
		outline(4),
	])

    btn.add([
		text(txt),
		anchor("center"),
		color(0, 0, 0),
	])

    btn.onClick(f)
	return btn
    addButton("Start", vec2(200, 100), () => start())
```
NOTE: The `btn.onClick(f)` makes it so that once the button is clicked, the "f" parameter runs. In this case, the button will go to `start()` which is the function that brings a user into the game. Vectors are points within the game scene. They are essentially coordinate points but with more functions relating to physics.

* I added a new tag on a portal sprite that I already added into the game and duplicated with a new symbol. The purpose of it was to make it so that one of the two portals would lead a user sprite to the losing scene.
    * This is a vital component of my desired product where a user has to answer a question between two portals that were answer choices.

```JS
  const LEVELS =
    "(": () => [
        sprite("pov"),
        area(),
        anchor("bot"),
        scale(.15),
        "danger",
  ],

  player.onCollide("danger", () => {
            go("lose", { score: score })
        })

  scene("lose", ({ score }) => {
        add([
            text(`You beat ${score} level(s)... Try again!`),
            pos(12),
        ])

```
NOTE: The ` { score: score }` code portion takes in the score at the moment when the user collides with a spike sprite. This makes it so that when the user sprite is sent to the "lose" scene, there would be a definite `score` value to display. If the code is not there, an error would run.

* I also learned the concept of hover. Using `hover()` and `hoverEnd()`, I was able to make my user sprite (nicknamed with the tag "nerd") change colors whenever it was being hovered on and not.

``` JS
nerd.onHover(() => {
	redBean.color = BLUE
})
nerd.onHoverEnd(() => {
	redBean.color = RED
})
```

Next Steps: Continue to learn more components and start to transfer most of my knowledge and resort to building a viable educational game with my partner


### 3/24/25
* I worked with Kyle this week and added new levels with unique block, trap, and coin placements
    * We also rearranged the symbols so that "=" represented blocks, "@" was the user sprite, and ">" were the spikes. The "$" represented the coins.

* I also worked with Kyle to add a new coin counter that was below the level one.
    * I declared a new variable `cScore` and set the value to an `add` component. Within the `add()`, I added a `text()` with the value `"Coins:" + " " + coinScore`. I also positioned the text to the top left corner of the game scene and used `fixed()` to keep it in place. I also made it so that the score was brought onto a new level by updating the game scene.
    * Kyle worked on adding `coinScore` onto the scene parameter and popping the coin and increasing the `coinScore` number count within the `.onCollide` function.

```JS
// Game Scene
scene("game", ({ levelIdx, stageScore, coinScore }) => {
 if (levelIdx < LEVELS.length - 1) {
    go("game", {
    levelIdx: levelIdx + 1,
    stageScore: stageScore,
    coinScore: coinScore,
    })
    } else {
    go("win", { stageScore: stageScore, coinScore: coinScore })
}

// Collision
player.onCollide("coin", (coin) => {
		destroy(coin)
		coinScore++;
		cScore.text = "Coins:" + " " + coinScore;
	})

// Coin Counter
const cScore = add([
		text("Coins:" + " " + coinScore),
		pos(15, 60),
        fixed(),
	])

```

NOTE: `levelIdx` represents the amount of levels within a scene. `coinScore` and `stageScore` have to be frequently called in all places in the code so the computer knows the updated value to display. Otherwise, an error would occur.

* I also adjusted the gravity of the userSprite so that it was challenging but still possible to make certain obstacle jumps:

```JS
    k.setGravity(1300);
```

* At last, I learned the concept of mass. I created a new block that had the used `body({ mass: 10})` and placed it in my game using the comma symbol.

``` JS
",": () => [
    sprite("block"),
    area(),
    scale(0.15),
    pos(0, 200),
    body({ mass: 10}),
    anchor("bot"),
],
```

NOTE: Mass makes a body not static. It gives it a weight that a user can push off.
Next Steps: Continue to work on my MVP with Kyle and make new revisions in the game

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
