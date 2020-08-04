# Step 9: Win or Lose

But what's this? If you play for long enough, even if your health goes down to zero, the game still continues! Not just that, you can continue to shoot at the enemys, too. That isn't going to work, now is it? You need some sort of a win/lose scenario to make the game worth playing.

So let's add the win and lose condition as well as the win or lose screen. :] You do this by exiting out of the main loop and going into a win/lose loop. In the win/lose loop, you have to figure out if the user won or lost and display the screen accordingly.

Here is a basic outline of the win/lose scenarios:

If time is up (90000 ms or 90 seconds) then:

* Stop running the game
* Set outcome of game to 1 or win

Calculate the accuracy.

`Note: The acc[0]*1.0 is just converting acc[0] to a float. If you do not do this, the division operand will return an integer like 1 or 2 instead of a float like 1.5`

Add these lines to the end of game.py:

```python
    #10 - Win/Lose check
    if pygame.time.get_ticks()>=90000:
        running=0
        exitcode=1
    if healthvalue<=0:
        running=0
        exitcode=0
    if acc[1]!=0:
        accuracy=acc[0]*1.0/acc[1]*100
    else:
        accuracy=0
# 11 - Win/lose display        
if exitcode==0:
    pygame.font.init()
    font = pygame.font.Font(None, 24)
    text = font.render("Accuracy: "+str(accuracy)+"%", True, (255,0,0))
    textRect = text.get_rect()
    textRect.centerx = screen.get_rect().centerx
    textRect.centery = screen.get_rect().centery+24
    screen.blit(gameover, (0,0))
    screen.blit(text, textRect)
else:
    pygame.font.init()
    font = pygame.font.Font(None, 24)
    text = font.render("Accuracy: "+str(accuracy)+"%", True, (0,255,0))
    textRect = text.get_rect()
    textRect.centerx = screen.get_rect().centerx
    textRect.centery = screen.get_rect().centery+24
    screen.blit(youwin, (0,0))
    screen.blit(text, textRect)
while 1:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            exit(0)
    pygame.display.flip()
```

This is the longest bit of code yet! But it’s not that complicated.

The first if statement checks if the time is up. The second one checks if the spacestation is destroyed. The third one calculates your accuracy ratio. After that, a quick if statement checks if you won or lost and displays the correct image.

Of course, if you want to display images for the win and lose screens, then those images have to be loaded first. So add the following code to the end of section #3:

```python
gameover = pygame.image.load("resources/images/gameover.png")
youwin = pygame.image.load("resources/images/youwin.png")
```

One more quick thing. Change section #4 from:

```python
# 4 - keep looping through
while 1:
    badtimer-=1
```

To:

```python
# 4 - keep looping through
running = 1
exitcode = 0
while running:
    badtimer-=1
```

The running variable keeps track of if the game is over and the exit code variable keeps track of whether the player won or lost.

Run the game again and now you can either triumph or die trying! Cool.

[<<< Last Step](./step8.md) | [Next Step >>>](./step10.md)
