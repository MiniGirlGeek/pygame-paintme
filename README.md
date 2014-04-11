# PyGame: Paintme

This is a drawing program for the raspberry pi that uses pygame. It's designed to be compatable with the Adafruit TFT.

## Step by Step Guide

1.  Open Idle (2.7, not 3)

2.  Click `File > New Window` or hit `Ctrl + N`

3.  Import the `pygame`, `sys`, `os` and `time` modules

    ```python
    import pygame
    import sys, os
    import time
    ```

4.  Initiate pygame

    ```python
    pygame.init()
    ```
5.  Next we'll set up the mouse and the frames per second clock.

    ```python
    mouse = pygame.mouse
    fpsClock = pygame.time.Clock()
    ```
6.  Now we'll set up our two displays:
    *  window
    *  and canvas
    
    ```python
    width = 320
    height = 240
    
    window = pygame.display.set_mode((width, height))
    canvas = window.copy()
    ```
7.  Next we'll set up some colors, for now we'll just use black and white but feel free to add more, you can do this by using an RGB color code, you can find these by using <a href="http://www.colorpicker.com/" target="_blank">this tool</a>
    ```python
    #                     R    G    B
    BLACK = pygame.Color( 0 ,  0 ,  0 )
    WHITE = pygame.Color(255, 255, 255)
    ```

    **note: you'll need to use the american spelling of color...unfortunately it will break if you spell it the corect way with a `u`**
8.  Now we'll build our window. Set up a forever loop and udate the display and add in an exit loop
    
    ```python
    while True:
      for event in pygame.event.get():
        if event.type == QUIT:
          pygame.quit()
          sys.exit()
      pygame.display.update()
    ```
    
    Save your code using `ctrl + s` and then press `F5`, a small black window should apear. Press the x to close it.

9.  Now we're going to fill in our window with a background colour, in this case it will be the white color we set up earlier. In the while True we created earlier enter the following line of code before `python pygame.display.update()`

    ```python
    window.fill(WHITE)
    ```
    
10. Save your code and run it again, you should now see that your screen is filled with your background color.

11. Next we're going to make a circle follow your mouse so as you can see where you'll draw. So we're going to find out where your mouse is using `pygame.mouse.get_pos()`. Inside the `while True` after the `window.fill(WHITE)` line add in the code that draws the circle at the cursor's position.
    ```python
    pygame.draw.circle(window, BLACK, (pygame.mouse.get_pos()), 5)
    ```
    Now if you save and run your code you should see a small black circle following your cursor around.

12. Now we need to give your program the ablility to check that your mouse is held down or not. To do this we going to add the following lines at the top of our `while True` loop.

    ```python
    left_pressed, middle_pressed, right_pressed = mouse.get_pressed()
    ```

    and in order to draw a circle when your mouse click is detected you'll have to add this code on to the end of our `for event in pygame.event.get()` loop, which can otherwize be known as an event handler.
    
    **Note: you must ensure it has the same level of indentation as your previous `if` statement**

    ```python
    elif left_pressed:
      pygame.draw.circle(canvas, BLACK, (pygame.mouse.get_pos()),5)
    ```
		
	If you save and run now you should be able to draw!

13. Finally we're going to give your window a title. Below `pygame.init()` add in the following line of code, you can replace paintme with whatever title for your game you want!

    ```python
    pygame.display.set_caption('Paintme')
    ```
## How to Extend your project.

> 1.  You could add the ability to change colors
> 2.  Or use the arrow keys to make the brush change size
> 3.  You could add in a clear button
> 4.  Or introduce the ability to save the image you have created
> 5.  Allow the user to import a picture, draw on top of it, and resave the image
>
> And much much more!
> You can find the codes for different key presses <a href='http://www.pygame.org/docs/ref/key.html' target='_blank'>here</a> and other pygame functionality <a href='http://www.pygame.org/docs/' target='_blank'>here</a>.


    
