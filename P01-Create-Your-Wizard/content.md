---
title: "Create Your Wizard"
slug: create-wizard
---

Now, let's start adding some magic. But first, we'll need a wizard!

> [action]
> Add `var wizard, pet, magicScroll, broom;
` to the **very top** of `sketch.js`, above `function setup()`

You've just declared 4 global variables that will be available for all of your code to access.

> [info]
> Variables are how you save and refer to existing objects or values.

Next up, make and save a `Wizard` to the `wizard` variable, and then call the `drawWizard()` function to make it appear.

> [action]
>
> 1. Inside of `setup()`, on a new line, add `wizard = new Wizard();`
> 1. Inside of `draw()`, on a new line, add `drawWizard();`
>

Run your program and you should now see a shadowy wizard form!

![shadowy wizard form](assets/shadow_wizard.png "Shadowy Wizard")

## Check

Take a moment to check your code so far.

> [solution]
>
>```js
> var wizard, pet, magicScroll, broom;
>
>function setup() {
>  createCanvas(400, 400);
>
>  wizard = new Wizard();
>}
>
>function draw() {
>  background("lightgray");
>
>  drawWizard();
>}
>```
>

# Coloring Your World

Time to bring your shadowy wizard to life with some colors.

> [info]
> There are 4 main ways to use the `color()` function to create colors.
>
> 1. `color(number);`  // grayscale, 0-255, 0 for black, 255 for white
> 1. `color("colorname");` // named colors
> 1. `color(number1, number2, number3);` // RGB (red, green, blue), 0-255 each
> 1. `color("#abcdef");` // hexcode colors
>

Try one of each.

> [action]
> On a new line at the end of `setup()`, paste in the following, which will create and assign colors to several properties on `wizard`:
>
>```js
>wizard.wandColor = color(200);  // grayscale, 0 for black, 255 for white
>wizard.hatColor = color("teal"); // named colors
>wizard.robeColor = color(100, 50, 200); // RGB (red, green, blue), 0-255
>wizard.skinColor = color("#9e81f4"); // hexcode colors
>```
>

<!--  -->

> [action]
> Play with the 4 ways of making colors by changing the values until your wizard has a custom appearance.
>

Explore by changing the numbers, color names, and hexcodes and seeing what happens.  Then you can [search for "color picker"](https://www.google.com/search?q=colorpicker&oq=colorpicker&aqs=chrome..69i57j0l5.3848j1j1&sourceid=chrome&ie=UTF-8) to find tools that will help you get the values for any color you desire.

> [action]
> Add a few more lines to give your `wizard` a name:
>
>```js
>wizard.magicalName = "Wizard";
>wizard.magicalNameColor = color("#e8b255");
>```
>

<!--  -->

> [action]
> Customize your wizard's name and the color of the letter on their chest.

You should now have a custom and colorful wizard in the middle of your canvas!

## Check

> [solution]
> ![custom colorful wizard](assets/colorful_wizard.png "custom colorful wizard")
>
>```js
>var wizard, pet, magicScroll, broom;
>
>function setup() {
>  createCanvas(400, 400);
>
>  wizard = new Wizard();
>  wizard.wandColor = color(200);  // grayscale, 0 for black, 255 for white
>  wizard.hatColor = color("teal"); // named colors
>  wizard.robeColor = color(100, 50, 200); // RGB (red, green, blue), 0-255
>  wizard.skinColor = color("#9e81f4"); // hexcode colors
>  wizard.magicalName = "Wizard";
>  wizard.magicalNameColor = color("#e8b255");
>}
>
>function draw() {
>  background("lightgray");
>
>  drawWizard();
>}
>```
>
