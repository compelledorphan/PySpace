# Step 1: Making a screen

```python
# 1 - Import library
import pygame
from pygame.locals import *

# 2 - Initialize the game
pygame.init()
width, height = 1550, 1000
screen=pygame.display.set_mode((width, height))

# 3 - Load images
player = pygame.image.load("resources/images/spaceship.png")

# 4 - keep looping through
while 1:
    # 5 - clear the screen before drawing it again
    screen.fill(0)
    # 6 - draw the screen elements
    screen.blit(player, (100,100))
    # 7 - update the screen
    pygame.display.flip()
    # 8 - loop through the events
    for event in pygame.event.get():
        # check if the event is the X button
        if event.type==pygame.QUIT:
            # if it is quit the game
            pygame.quit()
            exit(0)
```

Save the file into your game folder (the one where the resources subfolder is) and name it game.py.

Let’s go through the code section-by-section:

1. Import the PyGame library. This allows you to use functions from the library in your program.
1. Initialize PyGame and set up the display window.
1. Load the image that you will use for the spaceship.
1. Keep looping over the following indented code.
1. Fill the screen with black before you draw anything.
1. Add the spaceship image that you loaded to the screen at x=100 and y=100.
1. Update the screen.
1. Check for any new events and if there is one, and it is a quit command, exit the program.

[<<< Last Step](./readme.md) | [Next Step >>>](./step2.md)
