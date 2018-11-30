---
title: "Animate Your Castle"
slug: animate-castle
---

Right now your castle is pretty static, with no movement other than your wizard looking around. Let's bring things to life!

First let's give your `wizard` the ability to walk around, by adding another property `walkSpeed` and then calling a helper function that will update the position for you.
- Inside of `setup()`, add `wizard.walkSpeed = 0.5;`
- Inside of `draw()`, add `wizard.updatePosition();`

Now you should see your `wizard` walking towards wherever your mouse is.

But let's give you a little more control - instead of the `wizard` walking all of the time, let's change it to only update position when we have pressed the `SHIFT` key on the keyboard. To accomplish this, you'll add your first custom function!

- At the end of `sketch.js`, *after* the end of the `draw()` function, add:
```
function updateWizardPosition() {
  if (keyIsDown(SHIFT)) {
    wizard.updatePosition();
  }
}
```
This function has a small `if` statement that checks if the `SHIFT` key is currently being pressed, and if the answer is yes, or `true`, then it will call `wizard.updatePosition();`

- Back up in `draw()`, remove `wizard.updatePosition();` and replace it with a call to your new function: `updateWizardPosition();`

Now, your `wizard` should only walk towards the mouse when you are pressing the `SHIFT` button.

NOTE: Be sure to click onto the canvas first, otherwise the key press won't be correctly captured and your wizard won't walk.

Let's get your pet moving now too.

Just like we gave the `wizard` a `walkSpeed` we need to give one to the `pet`:
- Add a new property to the `pet` object:
```
pet = {
  x: 100,
  ...
  walkSpeed: 0.5,
}
```

Are you ready for your next function and an even bigger `if` statement?
- At the end of `sketch.js`, add:
```
function updatePetPosition() {
  if (pet.x > width) {
    pet.walkSpeed = pet.walkSpeed * -1;
  } else if (pet.x < 0) {
    pet.walkSpeed = pet.walkSpeed * -1;
  } else {
    // leave walkSpeed the same
  }

  pet.x = pet.x + pet.walkSpeed;
}
```
- Inside of `draw()`, add `updatePetPosition();`

Take a few minutes to examine the new function here. At the top is a 3-part `if else` statement.

The first `if` checks if the `pet` has walked past the right edge of the canvas (the variable `width` is automatically assigned to match the size of the canvas from `createCanvas`).

The second `else if` checks if the `pet` has gone off the left side of the canvas.

In either of those cases, `pet.walkSpeed` is multiplied by `-1` in order to reverse the direction the `pet` is walking.

Lastly, the `else` statement is for any time the `pet` is not of the edge, and should not alter `walkSpeed`. Here this is noted with a comment using `//`.

Positive speed walks to the right, negative to left, as the `pet.x` value is updated in the last line of the function.

Let's add one more touch of motion to warm up this castle - a nice roaring fire in the kitchen! To add this effect, you'll make a tiny change to an existing function inside of the `drawFunctions.js` file.

- Find the `drawKitchen()` function, and locate the `// draw fire` section, which looks like this:
```
// draw fire
var fireX = x + 15;
var fireY = y + 95;
fill("orange");

while (fireX < 40) {
  var flameHeight = 0;

  triangle(fireX, fireY, fireX + 10, fireY, fireX + 5, fireY - flameHeight);
  fireX += 7;
}
```
So far this code is using some *local* variables, `fireX`, `fireY`, and `flameHeight`. Local variables are defined, assigned, and used within a single code block, so these variables are not visible or available for use outside of the `drawKitchen()` function.

The part that we want to change is `flameHeight`. Right now it's set to `0`, which is why we don't see any fire.
- Change the value to `10` and see how the fire appears under the cauldron: `var flameHeight = 10;`

Another thing to notice is that the flames are created using a `while` loop. As long as the conditional statement `fireX < 40` is `true`, the contents of the loop are repeated. Notice that the value of `fireX` is updated each time it reaches the end of the loop. Eventually, `fireX` will increase until it is more than `40`, and the condition will be `false` and the loop is ended.

Since the code that assigns `flameHeight` is called again each time the loop starts, we can use it to change the value each time for a more lively fire effect. We can use a great helper function called `random()`.

- Replace `var flameHeight = 10;` with `var flameHeight = random(10,15);` and watch the flames come to life.

The two values passed to `random()` are the low and high numbers that you want it to randomly select from. So in this case the smallest a flame could be is `10`, and the biggest is `15`. Try out other values to create a bigger or smaller fire effect.
