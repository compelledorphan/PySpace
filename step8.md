# Step 8: Add a HUD with Health Meter and Clock

The game's progressing pretty well. You have your attackers, and you have your defender. Now all you need is a way to keep score and to show how well the spaceship is doing.

The easiest way to do this is to add a HUD (Heads Up Display) that shows the current health level of the spacestation. You can also add a clock to show how long the spacestation has survived.

First add the clock. Add the following code right before the beginning of section #7:

```python
    # 6.4 - Draw clock
    font = pygame.font.Font(None, 24)
    survivedtext = font.render(str((90000-pygame.time.get_ticks())/60000)+":"+str((90000-pygame.time.get_ticks())/1000%60).zfill(2), True, (0,0,0))
    textRect = survivedtext.get_rect()
    textRect.topright=[635,5]
    screen.blit(survivedtext, textRect)
```

The above code simply creates a new font using the default PyGame font set to size 24. Then that font is used to render the text of the time onto a surface. After that, the text is positioned and drawn onscreen.

Next add the health bar. But before drawing the health bar, you need to load the images for the bar. Add the following code to the end of section #3:

```python
healthbar = pygame.image.load("resources/images/healthbar.png")
health = pygame.image.load("resources/images/health.png")
```

The first is the red image used for the full health bar. The second is the green image used to show the current health level.

Now add the following code right after section #6.4 (which you just added) to draw the health bar on screen:

```python
    # 6.5 - Draw health bar
    screen.blit(healthbar, (5,5))
    for health1 in range(healthvalue):
        screen.blit(health, (health1+8,8))
```

The code first draws the all-red health bar. Then it draws a certain amount of green over the bar, according to how much life the spacestation has remaining.

If you build and run the program, you should have a timer and a health bar.

[<<< Last Step](./step7.md) | [Next Step >>>](./step9.md)
