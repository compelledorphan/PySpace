# Step 3: Let's make this bad boy fly

Next you need to add some actual gameplay elements, like making the spaceship respond to key presses.

To do that, first you’ll implement a good method of keeping track of which keys are being pressed at a given moment. You can do this simply by making an array of key states that holds the state of each key you want to use for the game.

Add the following code to game.py at the end of section #2 (after you set the screen height and width):

```python
keys = [False, False, False, False]
playerpos=[100,100]
```

This code is pretty self-explanatory. The keys array keeps track of the keys being pressed in the following order: WASD. Each item in the array corresponds to one key – the first to W, the second to A and so on.

The `playerpos` variable is where the program draws the player. Since the game will move the player to different positions, it’s easier to have a variable that contains the player position and then simply draw the player at that position.

Now you need to modify the existing code for drawing the player to use the new playerpos variable. Change the following line in section #6:

```python
    screen.blit(player, (100,100))
```

To:

```python
    screen.blit(player, playerpos)
```

Next, update the keys array based on which keys are being pressed. PyGame makes detecting key presses easy by adding event.key functions.

At the end of section #8, right after the block checking for event.type==pygame.QUIT, put this code (at the same indentation level as the pygame.QUIT if block):

```python
        if event.type == pygame.KEYDOWN:
            if event.key==K_w:
                keys[0]=True
            elif event.key==K_a:
                keys[1]=True
            elif event.key==K_s:
                keys[2]=True
            elif event.key==K_d:
                keys[3]=True
        if event.type == pygame.KEYUP:
            if event.key==pygame.K_w:
                keys[0]=False
            elif event.key==pygame.K_a:
                keys[1]=False
            elif event.key==pygame.K_s:
                keys[2]=False
            elif event.key==pygame.K_d:
                keys[3]=False
```

Wow! Those are a lot of lines of code. If you break it down into the if statements though, it’s not that complicated.

First you check to see if a key is being pressed down or released. Then you check which key is being pressed or released, and if the key being pressed or released is one of the keys you’re using, you update the keys variable accordingly.

Finally, you need to update the playerpos variable in response to the key presses. This is actually very simple.

Add the following code to the end of game.py (with one indentation level, putting it at the same level as the for loop):

```python
    # 9 - Move player
    if keys[0]:
        playerpos[1]-=5
    elif keys[2]:
        playerpos[1]+=5
    if keys[1]:
        playerpos[0]-=5
    elif keys[3]:
        playerpos[0]+=5
```

This code simply checks which of the keys are being pressed and adds or subtracts from the player’s x or y position (depending on the key pressed) to move the player.

[<<< Last Step](./step2.md) | [Next Step >>>](./step4.md)
