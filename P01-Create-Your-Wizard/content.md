---
title: "Create Your Wizard"
slug: create-wizard
---

Now, let's start adding some magic. But first, we'll need a wizard!

> [action]
> Add `var wizard, pet, magicScroll, broom;
` to the *very top* of `sketch.js`, above `function setup()`

You've just declared 4 global variables that will be available for all of your code to access.

> [info]
> In programming, variables are how you save and refer to existing objects or values.

Next up, make and save a `Wizard` to the `wizard` variable, and then call the `drawWizard()` function to make it appear.

- Inside of `setup()`, on a new line, add `wizard = new Wizard();`
- Inside of `draw()`, on a new line, add `drawWizard();`

Run your program and you should now see a shadowy wizard form! Now, time for some custom colors.

- On a new line at the end of `setup()`, paste in the following, which will assign colors to several properties on `wizard`:
```
wizard.wandColor = color(200);  // grayscale, 0 for black, 255 for white
wizard.hatColor = color("teal"); // named colors
wizard.robeColor = color(100, 50, 200); // RGB (red, green, blue), 0-255
wizard.skinColor = color("#9e81f4"); // hexcode colors
```
These are the 4 main ways to select colors with the `color()` function. (You can search for "color picker" online to find tools that will help you get the RGB or hexcode values you need.)

- Now paste in a few more line to give your `wizard` a name, and customize the color (feel free to use any style you prefer):
```
wizard.magicalName = "Wizard";
wizard.magicalNameColor = color("#e8b255");
```

Check - you should now have a custom and colorful wizard in the middle of your otherwise empty canvas.
