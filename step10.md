# Step 10: Gratuitous Music and Sound Effects!

The game's looking pretty good but how does it sound? It's a bit quiet, isn't it? Adding some sound effects can change the whole feel of a game.

PyGame makes loading and playing sounds super simple. First, you have to initialize the mixer by adding this at the end of section #2:

```python
pygame.mixer.init()
```

Then load the sounds and set the volume level at the end of section #3:

```python
# 3.1 - Load audio
hit = pygame.mixer.Sound("resources/audio/explode.wav")
enemy = pygame.mixer.Sound("resources/audio/enemy.wav")
shoot = pygame.mixer.Sound("resources/audio/shoot.wav")
hit.set_volume(0.05)
enemy.set_volume(0.05)
shoot.set_volume(0.05)
pygame.mixer.music.load('resources/audio/moonlight.wav')
pygame.mixer.music.play(-1, 0.0)
pygame.mixer.music.set_volume(0.25)
```

Most of the above code is simply loading the audio files and configuring the audio volume levels. But pay attention to the pygame.mixer.music.load line – that line loads the background music for the game and the next line sets the background music to repeat forever.

That takes care of the audio configuration. :] Now all you need to do is to play the various sound effects as needed. Do that as per the directions in the comments for the code below:

```python
# section 6.3.1 after if badrect.left<64:
hit.play()
# section 6.3.2 after if badrect.colliderect(bullrect):
enemy.play()
# section 8, after if event.type==pygame.MOUSEBUTTONDOWN:
shoot.play()
```

Run the game one more time and you'll notice that you now have background music and sound effects for collisions and shooting. The game feels that much more alive!

Boom.

[<<< Last Step](./step9.md) | [Conclusion >>>](./step11.md)
