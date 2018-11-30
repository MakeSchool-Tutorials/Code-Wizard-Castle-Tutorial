---
title: "Decorate Your Castle"
slug: decorate-castle
---

- Inside of `draw()`, add `drawCastle();` on a new line

Did you put it before or after `drawWizard()`? Try switching the order to see what happens.

Order matters! If you call `drawCastle()` last, your `wizard` looks like he is stuck in the floor, because the floor tile lines were drawn *after* the `wizard`.

- Put the two functions in the correct order so that the `wizard` is on top.

You now have a nice 4-room castle, nice! But remember that we still have 3 global variables for other objects we want to add to our code: `pet`, `magicScroll`, and `broom`.

So far, you've seen how to update values on an object using the `object.property = value` format. Now let's practice creating and assigning object values another way.

- At the end of the `setup()` function, add:
```
pet = {
  x: 100,
  y: 350,
  type: "cat",
  color: color("black"),
}
```
- Inside of `draw()`, add `drawPet();`
- Again, you can change the color
- Change the pet's location by adjusting the `x` and `y` values.

Notice that location `0, 0` is in the *upper left* corner, not the bottom left. So bigger `y` values are lower on the canvas.

- For help getting the exact coordinates, you can add the following helper code to the `draw()` function: `reveal(mouseLocation(), "mouseInfo");`
Now you should see the coordinates that your mouse is at on the top left corner above the canvase.

- If you don't want a `"cat"`, you can also try a `"frog"`, or `"ghost"`

Let's add information for the last two global variables:
- Inside of `setup()`, add:
```
magicScroll = {
  x: 300,
  y: 50,
}

broom = {
  x: 350,
  y: 350,
}
```
- Inside of `draw()`, add `drawScroll();` and `drawBroom();`
- Adjust the values so that the `magicScroll` is on the desk in the study, and the broom is by the fireplace in the kitchen.
