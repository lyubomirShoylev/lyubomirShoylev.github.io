---
layout: project
title: birthday card
description: an e-birthday card written in python
img: assets/img/proj-birthday-card-python/cake.png
github:
    user: lyubomirShoylev
    repo: zoBdayProj
    onpage: true
importance: 3
category: fun
---

In this project, I employed some stuff learned in a python book for beginners to create a birthday card for a friend that sings happy birthday to them (since I could not be present for the celebrations.)

## Goal

Since the book I was reading taught python by creating simple games with GUI in `tk`, I wanted to make a birthday card with a simple GUI. The key elements I wanted to implement were:

- Moving sprites
- Buttons that change stuff on screen
- Stages of stuff

Later, I came up with the ideas for the confetti and music playing.

## Intro pop-up

When opening the .exe file, you are greeted by a pop-up with a button to start the card playing. On clicking, the button closes the pop-up and starts the main program

## Main show

The main part of the card has several features. All the images are added the same way. We have images of: a birthday cake, party balloons, and a flame for the birthday candle. In addition, we have a rainbow of 'confetti', which are just drawn coloured circles, and some 'Happy Birthday' text in a funky font.

### Moving sprites

To make the card more interactive (and justify it being a programme rather than a simple image), we add a method to update the position of the confetti and balloons, which gives them the appearance of 'floating'. It does that by picking a random integer in the range $$[-2, 2]$$ and changing the sprite position with that many pixels. The number is different for each sprite and the two axes of each sprite (the vertical change for the confetti is in the range $$[20, 25]$$ to give the impression they are falling down). After that, the image canvas is updated.

The whole process is done once per millisecond.

### 'Make a wish' functionality

We include a button that prompts the user to 'make a wish' after some part of the birthday song has elapsed (see below). After clicking, it waits for some time, and 'blows the candle' i.e. removes the image sprite and updates the canvas.

## Happy birthday song

We include a method to play the birthday song using the computer beeper. It defaults to the speakers when they are present, but can also use the motherboard speaker if speakers are not available.

To enable the simultaneous execution of the GUI and sound playing, we had to use a second thread since they could not be played simultaneously on the single thread. This has to be done manually in python; our implementation uses `threading` library.

Note that the beeper sound is hard-coded using `winsound` and will only work on Windows machines. This was OK in our case since the intended recipient used a Win machine.

### Soundcheck

While trying to get the sound working, we found that the sound playing is a bit fiddly. To ensure the sound was working for the recipient without giving away the 'surprise', we also include a separate .exe to test the sound, `speakerTester.exe`.

## Executable files

After the code was written, we compiled to executable files the two scripts - the soundcheck and the b-day card. We use either PyInstaller or py2exe.

To make it more presentable, we used ResourceHacker to change the icon files to something a little more presentable.

## Conclusions

The project was a fun little experiment to test what I had learned while reading the book. It is not perfect by any metric, but given the time constraint, it turned out alright.

There are several things to improve to give it a more finished look:

- Remove the cmd window that starts alongside the app
- Add a counter for the candle flame
- Restrict the balloon movement to the borders of the canvas
- Think of a way to close the app with a dialogue box etc.
