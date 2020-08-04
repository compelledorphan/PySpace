# Step 7: Collisions with Enemies and Arrows

The enemies are attacking you but your arrows have no effect on them! How's an astronaut supposed to defend his home?

Time to set the arrows to kill the enemies so you can safeguard your spacestation and win the game! Basically, you have to loop through all of the bad guys and inside each of those loops, you have to loop through all of the arrows and check if they collide. If they do, then delete the enemy, delete the arrow, and add one to your accuracy ratio.

Right after section #6.3.1, add this:

```python
        #6.3.2 - Check for collisions
        index1=0
        for bullet in arrows:
            bullrect=pygame.Rect(arrow.get_rect())
            bullrect.left=bullet[1]
            bullrect.top=bullet[2]
            if badrect.colliderect(bullrect):
                acc[0]+=1
                badguys.pop(index)
                arrows.pop(index1)
            index1+=1
```

There's only one important thing to note in this code. The if statement is a built-in PyGame function that checks if two rectangles intersect. The other couple of lines just do what I explained above.

If you run the program, you should finally be able to shoot and kill the enemys.

[<<< Last Step](./step6.md) | [Next Step >>>](./step8.md)
