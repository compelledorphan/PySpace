# Step 6: Enemies Attack!

In this step, you’ll create randomly generated enemies that run across the screen. There will be more and more enemies as the game progresses. So, let’s make a list of what you’ll need it to do.

1. Add bad guys to a list an array.
1. Update the bad guy array each frame and check if they are off screen.
1. Show the bad guys.
Easy, right?

First, add the following code to the end of section #2:

```python
badtimer=100
badtimer1=0
badguys=[[1550,100]]
healthvalue=194
```

The above sets up a timer (as well as a few other values) so that the game adds a new enemy after some time has elapsed. You decrease the badtimer every frame until it is zero and then you spawn a new enemy.

Now add the following to the end of section #3:

```python
badguyimg1 = pygame.image.load("resources/images/badguy.png")
badguyimg=badguyimg1
```

The first line above is similar to all the previous image-loading code. The second line sets up a copy of the image so that you can animate the bad guy much more easily.

Next, you have to update and show the bad guys. Add this code right after section #6.2:

```python
    # 6.3 - Draw enemys
    if badtimer==0:
        badguys.append([640, random.randint(50,430)])
        badtimer=100-(badtimer1*2)
        if badtimer1>=35:
            badtimer1=35
        else:
            badtimer1+=5
    index=0
    for badguy in badguys:
        if badguy[0]<-64:
            badguys.pop(index)
        badguy[0]-=7
        index+=1
    for badguy in badguys:
        screen.blit(badguyimg, badguy)
```

Lots of code to go over. :] The first line checks if badtimer is zero and if it is, creates a enemy and sets badtimer up again based on how many times badtimer has run so far. The first for loop updates the x position of the enemy, checks if the enemy is off the screen, and removes the enemy if it is offscreen. The second for loop draws all of the enemies.

In order to use the random function in the above code, you also need to import the random library. So add the following to the end of section #1:

```python
import random
```

Finally, add this line right after the while statement (section #4) to decrement the value of badtimer for each frame:

```python
badtimer-=1
```

Try all of this code out by running the game. Now you should start seeing some real gameplay – you can shoot, move, turn, and enemies try to run at you.

But wait! Why aren't the enemies blowing up the spacestation? Let's quickly add that in...

Add this code right before the index+=1 on the first for loop in section #6.3:

```python
        # 6.3.1 - Attack spacestation
        badrect=pygame.Rect(badguyimg.get_rect())
        badrect.top=badguy[1]
        badrect.left=badguy[0]
        if badrect.left<64:
            healthvalue -= random.randint(5,20)
            badguys.pop(index)
        # 6.3.3 - Next bad guy
```

This code is fairly simple. If the enemies x value is less than 64 to the right, then delete that bad guy and decrease the game health value by a random value between 5 and 20. (Later, you will display the current health value on screen.)

[<<< Last Step](./step5.md) | [Next Step >>>](./step7.md)
