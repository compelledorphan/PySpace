# Step 4: Pulling 360s

Yes, your spaceship now moves when you press keys but wouldn’t it be even cooler if you could use your mouse to rotate the spaceship to face a direction of your choosing, so it's not facing the same way all the time? It’s simple enough to implement using trigonometry.

To do this, you can use the PyGame Surface.rotate(degrees) function. Incidentally, keep in mind that the Z value is in radians. :[

The atan2 function comes from the Python math library. So add this to the end of section #1 first:

```python
import math
```

Then, replace the last line in section #6 (the player.blit line) with the following code:

```python
    # 6.1 - Set player position and rotation
    position = pygame.mouse.get_pos()
    angle = math.atan2(position[1]-(playerpos[1]+32),position[0]-(playerpos[0]+26))
    playerrot = pygame.transform.rotate(player, 90-angle*57.29)
    playerpos1 = (playerpos[0]-playerrot.get_rect().width/2, playerpos[1]-playerrot.get_rect().height/2)
    screen.blit(playerrot, playerpos1)
```

Let’s go through the basic structure of the above code. First you get the mouse and player positions. Then you feed those into the atan2 function. After that, you convert the angle received from the atan2 function from radians to degrees (multiply radians by approximately 57.29 or 360/2π).

Since the spaceship will be rotated, its position will change. So now you calculate the new spaceship position and display the spaceship on screen.

[<<< Last Step](./step3.md) | [Next Step >>>](./step5.md)
