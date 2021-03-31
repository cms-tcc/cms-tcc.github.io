---
title: Python Basics
---

Here's how to set up Python on your Circuit Playground Express (CPX) board. This guide will also walk you through the basics of using Python.

## Installing Python
Download the latest version of CircuitPython from [here](https://circuitpython.org/board/circuitplayground_express/). Save it somewhere handy.

With the CPX plugged into your computer, double-click the `RESET` button. (It's the small one in the middle!) A USB drive named `CPLAYBOOT` should appear on your computer. (If double-clicking doesn't work, try a single-click.)

Drag the file you just downloaded onto `CPLAYBOOT`. You should get some [blinkenlights](https://en.wikipedia.org/wiki/Blinkenlights) and a new USB drive called `CIRCUITPY` should appear.

## Installing the Mu Editor
Install the Mu editor from [here](https://github.com/mu-editor/mu/releases/latest).

Mu is the easiest editor to get started with, please use it, unless you are an experienced coder with a favorite editor already!

When you first start Mu, you will be asked to choose a mode. Choose "CircuitPython" here.

### If you aren't using Mu
You'll need to use `screen` to see the output and use the REPL. 
On a Mac: In a terminal, type
```sh
screen /dev/cu.usb[TAB] 115200
```
Press the tab key where it says `TAB` to autocomplete the name of the port.

## Your First Program
Copy the below code and replace the code in Mu with it.
```py
from adafruit_circuitplayground import cp
import time

led = cp.red_led

while True:
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)
```
Save your code.

If everything worked, you should have a little red light blinking! Congratulations, you just wrote your first Python program. Welcome to electronics!

## Editing Code
Now go back to your code and change the two `0.5`s to `0.1`. The light should have changed. Let's find out why!

## Exploring the Program
Let's take a look at the code you're writing. Here's the original again:
```py
from adafruit_circuitplayground import cp
import time

led = cp.red_led

while True:
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)
```
### Imports
Each program needs to know what it'll need to get from its storage to be able to work. These items are called **libraries**. Some of them are built in, while others are stored on your `CIRCUITPY` drive in a folder called `lib`. 

```py
from adafruit_circuitplayground import cp
import time
```
These "import statements" tell the board that you're going to import some libraries. The first one, `from adafruit_circuitplayground import cp` tells the board, "Go into the `adafruit_circuitplayground` folder and grab the `cp` file." The `cp` library includes code to access all the features of the board. Check [the manufacturer's guide](https://learn.adafruit.com/circuitpython-made-easy-on-circuit-playground-express/circuit-playground-express-library) to see everything you can do. The next line, `import time`, tells the board to get the `time` functions. This lets you do things like going to sleep or checking how long the code has been running.

### Setting up
The next line, `led = cp.red_led` basically means "store `cp.red_led` in a variable called `led` so I can refer back to it later." Variables are ways to store values in code, like a player's score, or their name.

### Looping around
The last section starts with a `while True:` statement, which basically means "forever do:" Code will loop as long as what's after the word `while` is true, and because `True` is never false, it will run forever. Everything indented below the `while True:` is inside the loop.

There are four lines of code inside the loop. The first one, `led.value = True`, tells the LED to turn on. The next one, `time.sleep(0.5)`, tells the board to sleep, or wait, for 0.5 seconds. Then it does that again, turning the LED off. When you edited the code, it made the LED stay on for less time.

## Using the Serial Console
One common feature of programming is a "print statement". This is a line that causes your program to output some text. In Python, it looks like
```py
print("Hello, world!")
```
This print statement would result in "Hello, world!" But these print statements need somewhere to show. That's where the serial console comes in!

In Mu, find the "Serial" button in the toolbar and click it. 

Now add a print statement anywhere in your code. Here's one example:
```py
from adafruit_circuitplayground import cp
import time

led = cp.red_led

while True:
    print("Hello, world!")
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)
```
Now save the file. If you take a look at your serial window, you should see your print statement appear!

## Using the Console to Debug
Now, let's introduce an error to our code to see what happens.

Remove the last `e` from the `led.value = True` line so it says `led.value = Tru`. Save your code. The LED will stop blinking, and you might have a colored light flashing at you. Don't panic! Take a look at your serial console. There will be a few things in there. Let's break it down.

The `Traceback (most recent call last):` is telling you what it was doing when it crashed. Here, it's telling you that it got to line 8 of the `code.py` file. The next line is your error: `NameError: name 'Tru' is not defined`. This might not mean anything to you, but knowing that your error was on line 8, it gives you a great place to start your debugging. 

Go back to your code, and look at line 8. Obviously, you already know what went wrong. But if you didn't, you'd want to look at that line, or try googling the error. But in this case, you know what to look for - spelling True wrong. Fix the typo and save the file. Congratulations! You just fixed your first error! 

## The REPL
The other thing you can do over the serial console is use the REPL, or Read-Evaluate-Print-Loop. This allows you to enter lines of code and instantly run them. You can use it to debug a program line-by-line, or experiment with new code.

To use the REPL, connect to the serial console and press <kbd>CTRL + C</kbd> (yes, even on Mac). If there is code running, it will stop and you'll see "Press any key to enter the REPL. Use CTRL-D to reload." Follow those instructions, and press any key on your keyboard.

If there is no code running, you will enter the REPL immediately after pressing Ctrl + C. There is no information about what your board was doing before you interrupted it because there is no code running.

Either way, once you press a key you'll see a `>>>` prompt welcoming you to the REPL!

Here, you can run individual lines of code. Try running your blink program, one line at a time.

To exit the REPL, press <kbd>CTRL + D</kbd> (still even on Mac). This will restart your previous program.

## Don't stop there!
There's so much more you can do. Go [here](https://learn.adafruit.com/circuitpython-made-easy-on-circuit-playground-express/circuit-playground-express-library) for everything you can do, or [check here](https://learn.adafruit.com/category/express) for a few project ideas.
