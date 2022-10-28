from tkinter import*
import tkinter.font
from gpiozero import LED
import RPi.GPIO
RPi.GPIO.setmode(RPi.GPIO.BCM)

red = LED(17)
green = LED(27)
white = LED(22)

win = Tk()
win.title("LED Toggler")
SimpleFont = tkinter.font.Font(family= "hello", size = 12, weight = "bold")

def ledToggle():
    if red.is_lit:
        red.off()
        redledButton["text"]= "TURN THE RED LED ON"
    else:
        red.on()
        white.off()
        whiteledButton2["text"] = "TURN THE WHITE LED ON"        
        green.off()
        greenledButton1["text"] = "TURN THE GREEN LED ON"
        redledButton["text"] = "TURN THE RED LED OFF"

def ledToggle1():
	if green.is_lit:
		green.off()
		greenledButton1["text"] = "TURN THE GREEN LED ON"
	else:
		green.on()
		white.off()
		whiteledButton2["text"] = "TURN THE WHITE LED ON"
		red.off()
		redledButton["text"]= "TURN THE RED LED ON"
		greenledButton1["text"] = "TURN THE GREEN LED OFF"

def ledToggle2():
	if white.is_lit:
		white.off()
		whiteledButton2["text"] = "TURN THE WHITE LED ON"
	else:
		white.on()
		green.off()
		greenledButton1["text"] = "TURN THE GREEN LED ON"
		red.off()
		redledButton["text"]= "TURN THE RED LED ON"
		whiteledButton2["text"] = "TURN THE WHITE LED OFF"

def close():
    RPi.GPIO.cleanup()
    win.destroy()

redledButton = Button(win, font = SimpleFont, command = ledToggle, text = 'TURN THE RED LED ON', bg = 'red', height = 2, width = 25)
greenledButton1 = Button(win, font = SimpleFont, command = ledToggle1, text = 'TURN THE GREEN LED ON' ,bg = 'green', height = 2, width = 25)
whiteledButton2 = Button(win, font = SimpleFont, command = ledToggle2, text = 'TURN THE WHITE LED ON', bg = 'white', height = 2, width = 25)
Exitbotton = Button(win, text = 'Exit', font = SimpleFont, command = close, bg = 'orange', height = 1, width = 15)

redledButton.grid(row = 0, column = 0)
greenledButton1.grid(row = 1, column = 0)
whiteledButton2.grid(row = 2, column = 0)
Exitbotton.grid(row = 3, column = 0)
