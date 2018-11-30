---

title: "Get started with writing tutorials!"

slug: getting-started

---
### Step 5 - Interacting with Objects
It's time to add some interaction by giving your `wizard` some spells to cast.

Let's have your `wizard` cast a spell when you click the mouse.
- At the end of `sketch.js`, add:
```
function mousePressed() {
  wizard.castSpell();
}
```
This function is automatically called when you click the mouse on the canvas.

If you look in `wizardClass.js` at the `castSpell()` function, you can see that it will use the spell assigned to `.currentSpell`. If you try the program now you won't see any change because we haven't given the `wizard` a `.currentSpell` yet.

We'll add several different spells to use, so let's next add a function that will control which one to use based on which room the `wizard` is in.

- At the end of `sketch.js`, add:
```
function updateCurrentSpell() {
  if (false) {
    wizard.currentSpell = changeOutfitSpell;

  } else {
    wizard.currentSpell = noSpell;
  }
}
```
- Inside of `draw()`, add `updateCurrentSpell();`

Because the `if` condition is currently set to `false` it will always use the final `else` statement and assign `.currentSpell` to `noSpell`. If you look in `spellFunctions.js`, you'll see that `noSpell` doesn't do anything other than have the `wizard` say `Hmmmm...`. This is exactly what we want, so that there's always a backup assigned in case none of the other `if` conditions are true.

If you change `false` to `true`, then it will always assign the `changeOutfitSpell`. If you look closely, you may see that in `updateCurrentSpell` we aren't using `()` at the end of the function names - this is intentional!

In JavaScript, the way that you *call* or *perform* a function is by adding `()` to the end (with or without arguments). But in this situation, we just want to *refer* to the function. If you look at the `castSpell()` function in `wizardClass.js` again, you can see that it first checks if `currentSpell` has a value, and if so, then it calls the function with `()`:

```
castSpell() {
  if (this.currentSpell) {
    this.currentSpell();
  }
}
```

Getting back to the `updateCurrentSpell()` function, we don't want to hardcode `true` or `false`, we want to use some code that will be `true` or `false` depending on which area of the castle the `wizard` is in, so that we cast a different spell in each room. We'll do this by adding helper functions that `return` a boolean value (`true` or `false`).

- At the end of `sketch.js`, add:
```
function inBedroom() {
  if (wizard.x < width/2 && wizard.y < height/2) {
    return true;
  } else {
    return false;
  }
}
```
Now the condition of the `if` statement is a bit more complex, so let's break it down. The first part is checking if the wizard is in the left half of the canvas, by checking if `wizard.x` is less than (`<`) half the canvas (`width/2`). If the first part is `true`, the `&&` AND operator tells it to also check if the wizard is in the top half of the canvas by checking if `wizard.y` is less than (`<`) half the canvas height (`height/2`). When both of these conditions are `true`, the entire `if` is `true`. If either one is `false`, the whole thing is `false`.

- Inside of `updateCurrentSpell()`, change the first `if` condition to call the new helper: `if (inBedroom()) {`

Try it out, and see that when `wizard` is in the bedroom area that it uses `changeOutfitSpell()` but still uses `noSpell()` everywhere else. Right now only `wizard.wandColor` is changing.

- Go into `spellFunctions.js`, and modify `changeOutfitSpell()` so that it assigns all of the other color properties to a new color using the helper `randomColor();`

Awesome, right?!

Next up, you'll need to create the 3 missing helper functions - `inStudy()`, `inKitchen()`, and `inGreatRoom()` - that we'll need to assign 3 more spells for each room - `readScrollSpell()`, `levitateBroomSpell()`, and `transformPetSpell()`.

In the study your `wizard` will cast a spell to help read the `magicScroll`:
- Inside of `spellFunctions.js`, add:
```
function readScrollSpell() {
  wizard.say("Presto inko!");
  magicScroll.inkVisibility = 255;
}
```
- Inside `sketch.js` create a new `inKitchen()` helper.

Using `inBedroom()` as your example, you can create the missing function and modify the the `if` conditions to correctly compare the `wizard` `x` and `y` values with the room location. In addition to using `<` (less than), you may also need to use `>` (greater than). Be sure to combine two conditions to ensure the `wizard` is in the correct corner of the castle.

- Add a new `else if` condition in the middle of `updateCurrentSpell()`:
```
if (inBedroom()) {
  wizard.currentSpell = changeOutfitSpell;

} else if (inStudy()) {
  wizard.currentSpell = readScrollSpell;

} else {
  wizard.currentSpell = noSpell;
}
```

When you cast your new spell in the Study, you should see a magical message appear and then disappear on the scroll. The `readScrollSpell` resets `magicScroll.inkVisibility` back to the maximum value of `255` (same as the 0 to 255 range for colors). If you look in `drawFunctions.js` at the `drawScroll()` function, you'll see that it uses 3 other properties that you can adjust: `.message`, `color`, and `disappearSpeed`.

- In `setup()`, you can add and customize the extra properties:
```
magicScroll = {
  x: 380,
  y: 50,
  message: "Hello World",
  color: color("orange"),
  disappearSpeed: 1,
}
```

In the kitchen, your `wizard` will call `levitateBroomSpell()` - why sweep when you can use magic, right?
- In `spellFunctions.js`, add:
```
function levitateBroomSpell() {
  wizard.say("Levi broomi!");
  broom.levitate = !broom.levitate;
}
```
This spell uses the `!` (bang) to toggle the boolean `true` / `false` value of `broom.levitate`. So if `broom.levitate` is currently `true`, it will be assigned to `false`, and vice versa.

- Create your `inKitchen()` helper function
- Add a new `else if` inside of `updateCurrentSpell()` and assign `wizard.currentSpell` to `levitateBroomSpell` when `
inKitchen()` is `true`

Now your `wizard` has the power to levitate and move the `broom` with the mouse.

Lastly, in the Great Room, your `wizard` will practice transforming your `pet`.
- In `spellFunctions.js`, add:
```
function transformPetSpell() {
  wizard.say("Switcha petta!");

  var petTypes = [
    "cat",
    "frog",
    "ghost"
  ]

  var newType = random(petTypes);
  var newColor = randomColor();

  pet.type = newType;
  pet.color = newColor;
}
```

Previously you used `random` to select a number value from a range, but it can also be used to randomly select an item from a list - an `Array` object. `Array`s are created by putting values inside of square brackets `[]`. `petTypes` is an array of the possible `pet` types.

- Create your `inGreatRoom()` helper
- Add a new `else if` inside of `updateCurrentSpell()` to use `transformPetSpell` when `inGreatRoom()` is `true`
