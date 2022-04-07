# Step 5: Shoot, rocket, shoot!

Now that your spaceship’s moving around, it’s time to add a little more action. :] How about letting the spaceship shoot enemies using arrows? This is no mild-mannered astronaut!

This step is a bit more complicated because you have to keep track of all the arrows, update them, rotate them, and delete them when they go off-screen.

First of all, add the necessary variables to the end of the initialization section, section #2:

```python
acc=[0,0]
arrows=[]
```

The first variable keeps track of the player’s accuracy and the second array tracks all the arrows. The accuracy variable is essentially a list of the number of shots fired and the number of enemys hit. Later, we will be using this information to calculate an accuracy percentage.

Next, load the arrow image at the end of section #3:

```python
arrow = pygame.image.load("resources/images/bullet.png")
```

Now when a user clicks the mouse, an arrow needs to fire. Add the following to the end of section #8 as a new event handler:

```python
        if event.type==pygame.MOUSEBUTTONDOWN:
            position=pygame.mouse.get_pos()
            acc[1]+=1
            arrows.append([math.atan2(position[1]-(playerpos1[1]+64),position[0]-(playerpos1[0]+64)),playerpos1[0]+64,playerpos1[1]+64])
```

This code checks if the mouse was clicked and if it was, it gets the mouse position and calculates the arrow rotation based on the rotated player position and the cursor position. This rotation value is stored in the arrows array.

Next, you have to actually draw the arrows on screen. Add the following code right after section #6.1:

```python
    # 6.2 - Draw arrows
    for bullet in arrows:
        index=0
        velx=math.cos(bullet[0])*10
        vely=math.sin(bullet[0])*10
        bullet[1]+=velx
        bullet[2]+=vely
        if bullet[1]<-64 or bullet[1]>640 or bullet[2]<-64 or bullet[2]>480:
            arrows.pop(index)
        index+=1
        for projectile in arrows:
            arrow1 = pygame.transform.rotate(arrow, 360-projectile[0]*57.29)
            screen.blit(arrow1, (projectile[1], projectile[2]))
```

The vely and velx values are calculated using basic trigonometry. 10 is the speed of the arrows. The if statement just checks if the bullet is out of bounds and if it is, it deletes the arrow. The second for statement loops through the arrows and draws them with the correct rotation.

[<<< Last Step](./step4.md) | [Next Step >>>](./step6.md)
