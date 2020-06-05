# Code for GUI toggler window

    from tkinter import *
    import tkinter.font
    from gpiozero import LED
    import RPi.GPIO as GPIO

    GPIO.setmode(GPIO.BCM)

    #set the pins connected to my LEDs as LED pin
    blue = LED(4)
    green = LED(25)
    red = LED(12)

    gui = Tk()
    gui.title("GUI LED TOGGLER")
    font = tkinter.font.Font(family = 'Athelas', size = 14, weight = 'bold')


    def toggleBlueLED():
        if blue.is_lit:
            blue.off()
            blueBtn["text"] = "TURN BLUE LED ON"
        else:
            blue.on()
            blueBtn["text"] = "TURN BLUE LED OFF"

    def toggleGreenLED():
        if green.is_lit:
            green.off()
            greenBtn["text"] = "TURN GREEN LED ON"
        else:
            green.on()
            greenBtn["text"] = "TURN GREEN LED OFF"

    def toggleRedLED():
        if red.is_lit:
            red.off()
            redBtn["text"] = "TURN RED  LED ON"
        else:
            red.on()
            redBtn["text"] = "TURN RED LED OFF"

    def exitWindow():
        GPIO.cleanup()
        gui.destroy()

    blueBtn = Button(gui, text = 'TURN BLUE LED ON', font = font, command = toggleBlueLED, bg = 'blue', height = 1, width = 20)
    blueBtn.grid(row = 0, column = 1)

    greenBtn = Button(gui, text = 'TURN GREEN LED ON', font = font, command = toggleGreenLED, bg = 'green', height = 1, width = 20)
    greenBtn.grid(row = 1, column = 1)

    redBtn = Button(gui, text = 'TURN RED LED ON', font = font, command = toggleRedLED, bg = 'red', height = 1, width = 20)
    redBtn.grid(row = 2, column = 1)

    exitBtn = Button(gui, text = 'EXIT', font = font, command = exitWindow, bg = 'grey', height = 1, width = 5)
    exitBtn.grid(row = 3, column = 1)
