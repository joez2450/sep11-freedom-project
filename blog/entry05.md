# Entry 5
##### 4/21/25

Since the last blog, I have worked with Kyle to create a minimal viable product for our idea of creating an educational game, which aimed to combat against the lower attention rates due to internet doom scrolling. Starting on a new file, we started to add new components that improved the interactive play.

Our first step was delegating tasks between two people through an [MVP plan](https://github.com/kylel5957/Kyle-Joe-Kaboom/blob/main/plan.md), where we added desired features (such as number of levels, types of questions, and sound effects) and a timeline to construct them. Afterward, we moved onto adding more features that aren't necessary for the minimal functionality, but would enhance the game.

Starting with the coding process, I first imported any functions that would benefit the game into the new file. I then created around eight levels throughout separate days. Before that, I had to ensure that the sprites were properly scaled (`scale`), positioned(`pos`), and attached to the right tags (to allow our functions that we imported to work) before adding them into the game scene. Within a `LEVELS` variable, I created brackets and symbols within them that represented the different sprites that were to be included in the game, making each layout distinct. Moreover, I created additional symbols that represented questions and answer choices, which I used `text` to display the words.

Kyle on the other hand, focused on creating sound effects. He imported three different audio files using `.loadSprite`, one to represent death, jump, and coin collection. He then incorporated them into existing functions and indicated specific tags for them to work. In addition to this, I also helped to create a second counter, but for coins. The one Kyle created didn't function as well since it removed the "Coins:" text and completely substituted with a number instead when you collected a coins. I revised the counter by concatenating "Coin:" with `coinScore`, which held the number of collected coins.

``` JS
// Before
player.onCollide("coin", (coin) => {
 		destroy(coin)
 		// play("pop")
 		coinScore++;
 		cScore.text = coinScore; // Adjusted to a number
 	})


// After
player.onCollide("coin", (coin) => {
		destroy(coin)
		play("coin")
		coinScore++;
		cScore.text = "Coins:" + " " + coinScore; // Coin: num
	})

```

### EDP
Currently, I am on the sixth stage of the Engineering Design Process. Kyle and I have already creating a prototype that is functional through coordinated plans and weeks of coding. The next step forward is to evalute the effectiveness of the prototype at tackling our aim. Afterward, we can move on to make any last revisions on our game before communicating the results to a broader audience.

### Skills
#### Adaptability
Since I was working with a partner, I had to be adaptable in order to maximize productivity. For instance, some days we may fall behind on our schedule due to difficulties in creating specific features. However, I would change the timeline and add the certain feature to be due on the same date of other tasks so we could focus on our issue and not stress as much. Additionally, when there were issues that my partner faced, such as updating a coin counter, I would help him out before moving on with my own tasks.

#### Teamwork
While building a minimal viable product, I have enhanced my teamwork ability working with Kyle. We had to tell each other when to pull changes or push any new code. In addition, I also had to communicate frequently to get on the same page as Kyle and know when to help out on a specific issue that was encountered or adapt to a revised priority on our MVP plan.


[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
