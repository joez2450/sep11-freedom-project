# Entry 1
##### 10/28/24
#### Context
For the first few weeks of the Freedom Project, I had been tinkering with one tool: [Kaboom](https://kaboomjs.com/). The tool is a game engines that can be used to make an interactive app. For this year's project, I am devoted to make an Education App that will include trivia which educate users while entertaining them. I decided to pair up with Kyle, who will be my year-long partner, as we both share the same interest regarding apps.

#### Choosing a Tool
Before choosing to stick with Kaboom, Phaser was also a tool option for my project idea. The way I distinguished between the two tools was through the process of tinkering.

For [Kaboom](https://kaboomjs.com/), I looked through the [intro documentation](https://kaboomjs.com/doc/intro) and imported a repository displayed on the site, which included all nessesary files for a interactive scene and a main codespace into my local IDE. The first components I learned was sprites and the method used to load them into a game scene, which used the `loadsprite` syntax. Afterward, I tested out the concepts of positioning and text using the `add()` game objective and `pos()` and `text()` components. Learning these concepts, I moved onto shapes and displayed rectangles onto a scene using `rect()`. I added loops using `loop(1)` to make the primitives reoccuring in the game scene at a set time of 1 second. At last, I made the sprite able to jump and added a new effect that would only occur when a collision takes place with the primitives. To do this, I added a body to the sprite using `body()` and implemented `.jump()` inside of a `onKeyPress` objective. Next, I used `shake()` in a `.onCollide` objective with a key phrase. As the final step, I used the phrase and placed it into the `add` objective that the primitive is in to allow the effect to take place for the specific shape.

On the other hand, my tinkering process for Phaser was not as smooth in comparison to Kaboom. I watched various videos and was able to import templates. I previewed various set codes inside of the main files and used `npm run dev` to see the game scene in action. Although this was the case, I was having trouble setting up my own workspace. Even with tutorials, I wasn't able to set up a local server and a functioning local working space. However, in the imported workspaces, I modified some of the code using `platforms.create(750, 220, 'ground');` to create obstacles. Additionally I learned the purpose of various functions such as `preload`, `update`, and `create`. Yet, the tinkering experience left me with a mixed feeling with the tool.

I chose Kaboom over Phaser because it includes many features that can be directly used to my creation such as `onKeyPressed`. While Phaser is a tool that can be applied for games, Kaboom is more efficient for my overall idea of an interactive app. The tool is also less difficult, which allows me to freely work while minimizing trouble that would interfere with my product. Thus, it will be my main tool for the remainder of the year.

#### EDP
As of now, I am on the first stage of the Engineering Design Process, which is to define a problem. An issue I wish to solve with Kyle using JavaScript this year is to improve the educational learning of many who have a low attention span and struggles without a digital screen. In order to make a product to tackle this issue, I would have to research more about my tool and work effectively with Kyle throughout the year.

#### Skills
##### Effective Researching:
One skill I improved on was Effective Researching. Throughout the whole tinkering process, I had to preview many documentations in order to learn the gist of my tools. This could only be done if I searched for the most important links. For instance, instead of looking at the tutorial on the Kaboom main page, which only provided the basic instructions for a local setup, I would search "Kaboom Intro". This brought me to a page where the creators provided instructions to make a simple game.

##### Time Management:
Another skill I improved on was Time Management. Since I had multiple tools on my list to use for the Freedom Project, I needed to be wise and efficient with my time in searching for the best option. As an example, during my Phaser tinkering I spent multiple days to learn the tool. Despite only reaching the basic level of the tool, I learned to move on and acknowledge that Phaser would pose more challenges during my Freedom Project journey, whereas Kaboom is still difficult but more manageable includes many features which I envision could be implemented into my game idea.



[Next](entry02.md)

[Home](../README.md)
