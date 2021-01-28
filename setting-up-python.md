---
title: Setting Up Python on the Circuit Playground Express
---

Here's how to set up Python on your Circuit Playground Express (CPX) board.

## Installing Python
Download the latest version of CircuitPython from [here](https://circuitpython.org/board/circuitplayground_express/). Save it somewhere handy.

With the CPX plugged into your computer, double-click the `RESET` button. (It's the small one in the middle!) A USB drive named `CPLAYBOOT` should appear on your computer. (If double-clicking doesn't work, try a single-click.)

Drag the file you just downloaded onto `CPLAYBOOT`. You should get some [blinkenlights](https://en.wikipedia.org/wiki/Blinkenlights) and a new USB drive called `CIRCUITPY` should appear.

## Installing the Mu Editor
Install the Mu editor from [here](https://github.com/mu-editor/mu/releases/tag/1.1.0-alpha.2).

Mu is the easiest editor to get started with, please use it, unless you are an experienced coder with a favorite editor already!

When you first start Mu, you will be asked to choose a mode. Choose "CircuitPython" here.

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

## Don't stop there!
There's so much more you can do. [Check here](https://learn.adafruit.com/category/express) for a few project ideas.
