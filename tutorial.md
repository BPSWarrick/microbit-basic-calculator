# BPS micro:bit Basic Calculator Tutorial 
 
### @explicitHints true 
### @activities true 


```template
//
```


## Introduction
### Introduction @showdialog
Welcome!


Hopefully by the end of this tutorial, you should be able to use the micro:bit as a basic calculator.

Select OK to continue. 


### Part 1 - Introduction @showdialog
This project heavily relies on ``||variables:variables||``.

Variables are a method to store a value which can be used later in a program.

If the program changes the value stored in the variable, it can go back to that variable to use the new value.

With a calculator (or in this case, a simple adding machine), the current number is stored in a variable. When the user creates an input, the micro:bit will take the new number and add it to the existing one inside the variable.

This project in particular will utilise two variables, one to keep in memory (existing number) and one to store the new number (one to be added).

### Part 1 - Step 1
First, you will need to create the two variables.

In the ``||variables:Variables||`` toolbox, select "Create new Variable..." and name the first one 'register'.

Create a second variable, and name it counter.

Now, drag in two ``||variables:set||`` blocks and place them in the ``||basic:on start||`` block and change one so you have one of each.
```blocks
let register = 0
let counter = 0
```

### Part 1 - Step 2
You will want a way to enter in a new number. Drag a ``||input:on button||`` block from the ``||input:Input||`` toolbox and place it on the canvas.

Next, drag in a ``||variables:change||`` block and place it inside the ``||input:on button||`` block.

To show what the current number is, pull in a ``||basic:show number||`` block and place it under the ``||variables:change||`` block.

Finally drag the ``||variables:counter||`` variable into the oval of the ``||basic:show number||`` block.
```blocks
input.onButtonPressed(Button.A, function () {
    counter += 1
	basic.showNumber(counter)
})
```

### Part 1 - Step 3
Now, you will need to duplicate what you just did in the last step. You can do this by selecting the ``||input:on button||`` block, right click (or two-finger click if on a chromebook) and select "Duplicate".

Change the button to be [B], and change the value in the ``||variables:change||`` under button [A] to -1.

This makes it so that the left button [A] will choose a lower number and the right button [B] will choose a higher number.
```blocks
input.onButtonPressed(Button.A, function () {
    counter += -1
	basic.showNumber(counter)
})
input.onButtonPressed(Button.B, function () {
    counter += 1
	basic.showNumber(counter)
})

### Part 1 - Step 3
Now that you have the ability to store a number into memory, you need to make an input which will add the current number to the stored number.

Grab a ``||input:on button||`` block and change the button to [A+B]. This means you use both buttons at the same time.

Drag in a ``||variables:set||`` block to inside the new ``||input||`` block and change it to ``||variables:register||``.

Do this again, but with changing the ``||variables:set||`` to ``||variables:counter||``.

Next, pull in a ``||basic:show number||`` block to go under the last ``||variables:set||`` block.
```blocks
input.onButtonPressed(Button.AB, function () {
    register = 0
	counter = 0
	basic.showNumber(0)
})

### Part 1 - Step 4
So at the moment, all you have is an input which resets everything. Now you need to add the two values together.

Under the ``||math:Math||`` toolbox there are a whole heap of 'operators'. Grab the first one (it has the + sign on it) and put it into the oval of the ``||variables:set [register]||``.

Next, drag in the ``||variables:register||`` variable and place it in the left-oval of the ``||math:Math||`` operator. Do the same with the ``||variables:counter||``, but put it in the right-oval of the operator.

### Part 1 - Step 4 Explainer @showdialog
What you just did is make it so the micro:bit will take the number stored in ``||variables:register||`` and add it to ``||variables:counter||`` and show the result.

Now since the only ``||variables:variable||`` that can be changed by the user is ``||variables:counter||``, that means at the beginning ``||variables:register||`` is zero (0) - so the first addition you do will always be the number that was just entered.

### Part 1 - Step 5
Finally, you will need a way to clear the micro:bit's memory so you can start again. For that, you can use the ``||input:on [shake]||`` input.

Drag in the input and place it on the canvas.

Next, pull down two ``||variables:set||`` blocks and put them inside the new ``||input:Input||`` block.

Then grab a ``||basic:show number||`` and put it at the bottom of the ``||input:on [shake]||`` block.

Change one one of the ``||variables:set||`` blocks so that you have one of each and then get the ``||variables:register||`` variable and put it inside the ``||basic:show number||`` block.
```blocks
input.onGesture(Gesture.Shake, function() {
    counter = 0
	register = 0
	basic.showNumber(register)
})

### Part 1 - Step 6
See if the program works by using the demo micro:bit on the left.

If it does, download it to your micro:bit and test.

