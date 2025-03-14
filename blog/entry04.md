# Entry 4
##### 3/10/25

Since the last blog, I have continued to learn new components and engaged in more peer programming with my partner Kyle as we previously merged works and began to develop a game together with features brought in from both of our original games. I was able to make new features that serve a purpose in my creations through learning lessons, which consisted of reviewing syntax documentation and blogs.

The first component I learned to build was a camera movement that always followed the user sprite. I wanted to revise my previous game with this feature as it was zoomed out and difficult to play among varying screen sizes. In the Kaboom playground, I learned of the combination `onUpdate`, `camPos`, and `onPhysicsResolve` with my `user` variable.

I created two distinct functions that applied to the user sprite `player`. In the first one, I included an `onUpdate` to `player` and within the function, I added a `camPos` that acted dynamically with `player.worldPos()`, which represented the coordinate plane in the game scene. Within the second function, I added `.onPhysicsResolve` to `player` and reused the same camera position code. These two functions combined ensured a smooth and functional camera tracking device for the user. The `.onUpdate` always followed the user sprite. The `onPhysicsResolve` made it so that as the user was jumping, the tracking would not be laggy.


```JS

	player.onUpdate(() => {
		camPos(player.worldPos())
	})

	player.onPhysicsResolve(() => {
		camPos(player.worldPos())
	})

```

The next component I learned was creating a pause menu. I knew that this feature would be a vital component of my game, and so I followed the documentation and playground example as my reference points. First off, I created a new variable `pause` that held a value of null, which was to be used later on. I then used `keyPress` and made it so that when the user pressed "p" a function would run. Afterward, I created a code that checked if the game was paused using the statement `game.pause = !game.pause`.


I went ahead and started making the pause menu shape that would show up. I declared a new variable `menu` which included a `rect`, `color`, `outline`, and `position` that I put to make a white rectangle with a semi-weight border show up at the middle of the screen. I then added an animation using another conditional with `tween()` so that when `userPause` was true, `menu` would ease into the middle. If the pause already occured, the `userPause.cancel()` would ease out the `menu`. The final changes I added was to make everything funcitonal. I created a new conditional that checked if `game.paused` was true, the `menu` variable would show up. If it was false, the opposite would happen by ending `userPause`.


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


The last feature I focused on were background colors, which was less complex to tackle. I wanted to switch my game from the default background scene, where there were only grey and white tiles to a lighter blue color. To do this, I used the `background()` property, which I used the RGB values of `206, 242, 241` to find the color I was satisfied with. My next plan is to create a separate portal that distinguishes a right and wrong answers for each question. Additionally, I will add coins and spikes to create an objective and challenge into the game.

### EDP
Currently, my partner and I are on the fifth stage of the Engineering Design Process, which is to create a prototype. We have gone through planning the most promising solution with our brainstorming of our [MVP and Beyond MVP Plans](https://github.com/kylel5957/Kyle-Joe-Kaboom/blob/main/plan.md). In the following weeks, I will work on creating levels with Kyle while also developing aesthetic features to reach a minimum viable product. Afterward, we will add additional features that will further improve my creation and also evaluate our prototype.


### Skills

#### Time Management
As the year keeps going by, major exams are also starting to come closer by day. In addition, with the heavy workload between all of my classes, which includes AP and honors, and activities that I am involved in, I had to time manage effectively in order to learn my tool. To do this, I set aside a specific portion of the day dedicated to learning Kaboom and the other delegated time is used to complete my daily tasks.

#### Organization
Since there are more components within my game that I incoporated features with Kyle, I started to comment on different parts of my code by writing a small amount of description that described each function. This helped me minimize confusion when I reviewed my game file. It also allowed me to stay on top of everything, so when I did encounter a error in the console, I was able to directly go to the lines of code responsible for the issue.



[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
