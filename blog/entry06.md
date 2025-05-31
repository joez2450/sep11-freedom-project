# Entry 6
##### 5/16/25

Ever since the last blog, I have modified my MVP with Kyle with Beyond MVP suggestions that were given to us during a gallery walk activity in class. The most called for feature was checkpoints.

Kyle and I thought out how to exactly make a checkpoint. We came up with an idea to use conditionals to receive an input from the user as to which level they wanted to go to. However, we wanted to also make it so that a user could only teleport back to either a level they are currently on or previously achieved.

Working together on this feature, Kyle created a new variable `levelWhat` which asked a user the prompt of which level they wanted to restart at. We added `parseInt` to convert the user's string response to an integer to compare it later on using operators. We then added a new conditional that checked if `levelWhat` was either greater than or equal to `stageScore`, which stored the level index. If the condition was satisfied, a `go` function would run, bringing a user back into the game scene. We set the `levelIdx` to be `levelWhat - 1` since it acts as an array and the levels were organized based on zero-based index counting. We also set the `coinScore` to zero and `stageScore` to `levelWhat` to reset the coin counter and match the level that the user desires to go back to.

After we completed the checkpoint, we created [presentation slides](https://docs.google.com/presentation/d/1mTrfeChYqEtcRuY7IsrA-1njXC6Yskf18GUQ0UwnznY/edit?slide=id.p#slide=id.p) that included our purpose of the game, process, challenges, and takeaways. For the in-class presentation, Kyle and I made a plethora of slides, trying to keep each of them short yet concise and meaningful. Towards the Expo showcase, we created a [plan](https://docs.google.com/document/d/1ylNxJGM-KGyNrMjxONf0UxuXADEex8unsTu4ZqD4j3c/edit?tab=t.0) and edited our slides based on it and hid some so that the presentation was quick enough to fit within the 1 minute timer and conveyed our main points.


### EDP
Currently in the Engineering Design Process, I have already completed the seventh stage which was to improve our products as needed. I added a new checkpoint feature where users could teleport to either their current or previous acheived levels so it reduces redundancy of having to restart the game if you answer a question incorrectly. I have also completed the eighth stage: Communicate Your Results. I have created presentation slides and an elevator pitch to present to the class and also at the Expo.

### Takeaways/Skills

#### Ending Off a Presentation
After presenting in class with Kyle, I reviewed the feedback that Mr. Mueller sent us. I learned that a presentation should typically end off with a "Thank You" and nothing else in the slide. In our case, we did end off with a "Thank You" but we added a shortned link to our product, making our presentation less logical. I learned to next time put the URL separately prior to the "Thank You" slide that would conclude the presentation.

#### Less is More
During the Expo showcase, Kyle and I learned that elevator pitches had to be condensed to ideally 3-4 slides while containing small text but that also captured the essence of the project. While we presented, I realized that we had a little too much slides to present within the one-minute time mark, which limited the amount of time we could have delegated towards our live demonstration of the platformer game.


[Previous](entry05.md) | [Next](entry07.md)

[Home](../README.md)
