# Dotstar-MicroPython-Module
Micropython module to use Dotstar tri-colour LEDs, Testing done with a Pi Pico microcontroller and an Adafruit 8x8 Dotstar grid

created Apr 25, 2023
modified Apr 27, 2023

Connections to the Dotstar grid/string are as follows:
- Pi Pico VBUS – Dotstar Vin (+5V connection)
- Pi Pico GND – Dotstar GND
- Pi Pico GP19 – Dotstar Din (data line)
- Pi Pico GP18 – Dotstar Cin (clock line)

Basic usage

Individual LED format - (R, G, B, Brightness) with R, G, B between 0-255 and Brightness #between 0-31 or -1 to denote using default brightness (dots.brightness)

brightness hierachy 
- individual led value if not -1
- brighness value passed with show() function
- default/dots.brightness value 

#initialize dotstar object

dots = DotStar(sdo = 19, clk = 18, numLEDs = 64, brightness = 3,  baudrate = 1000000, auto_write = False)
    
#set all LEDS to the same colour

dots.fill((150,0,0,-1)) - # set all LEDS to red at default brightness

dots.show()   
    
#set individual leds or range of leds

dots[0] = (0, 150, 0, 5)

dots[8:15] = [(0, 0, 150, -1)] * 8 

dots.show()  
        
 #change default brightness to 15
 
dots.brightness = 15 

#show using a different brightness level

dots.show(brightness = 9)  
  
#print current colour & brightness value for an led

print(dots[31])    
    
#methods to turning LEDS off

dots.fill((0,0,0,0))

dots.show()

#or     

dots.show(brightness = 0) # maintains last colour values
