---
title: Expressions
description: expressions
---

## Expressions in After Effects

When you want to create complex animations and link them together without manually creating dozens or even hundreds of keyframes, you can use expressions. An expression is like a short script that calculates the value of a property of a layer at a specific moment. It also allows you to establisg relationships between different layer properties. After Effects uses a JavaScript-based language to write these expressions.

### Adding an Expression

To add an expression to a property, `Option + click` on the stopwatch next to that property. A text box will appear where you can enter the expressions.

You can type the code entirely by hand or use preset snippets via the arrow next to the text box.

### Using Expressions and Keyframes Together

Even after adding an expression, you can continue using keyframes to animate specific values. For instance, the following expression applied to the rotation property of a layer increases the current value by 90 degrees: `value + 90;`.

If you then add keyframes to animate the original value, for example, from 0 to 90 degrees, the expression will automatically increase these values by 90 degrees.

### Dynamix Effects with Expressions

Some expressions automatically adjust a property's values. A well-known example is the wiggle expression. Pase this code onto a layer's position property and watch the effect: `wiggle(10, 10)`.

This causes the layer to shift 10 times per second by 10 pixels on both x and y axes. The first value determines how many times per second the change occurs, while the second value defines the magnitude of the change in pixels.

Expressions allow you to create animations more efficiently and intelligently, giving you more to focus on creativity instead of endlessly placing keyframes.

## Editing Expressions in After Effects

### Deactivating and Removing Expressions

You can temporarily disable an expression at any time by clicking the `=` icon next to the expression. The icon will change to `/=`, indicating the expression is deactivated. If you want to remove the expression entirely, `Option + click` on the property's stopwatch again.

### Linking Properties with the Expression Pick Whip

Next to the snippets icon, there's another tool: the Pick Whip. This functions differently from the standard layer pick whip. While the layer pick whip is used to parent layers, the expression pick whip links properties.

In the example below, the rotation of Square A is linked to the rotation of Square B using the Pick Whip. This method is often simpler than entering the code manually. When you adjust Square B's rotation, Square A will automatically follow.

> Note: Since Square A's rotation is linked to Square B's, you can no longer directly adjust Square A's rotation.

### Comments in expressions

Just like in JavaScript, you can add comments in your code to make it more readable.  
There are two ways to do this:

- Inline Comments: Use `//` to mark everything adter is on the same line as a comment.
- Block Comments: Use `/*` and `*/` to mark pultiple lines as comments.

### Basic Rules for Expressions in After Effects

- An expression always uses the value from the last statement in the code.
- The language is case-sensitive, so be mindful of capitalisation.
- Each statement must end with a semicolon (;).
- Spaces between words do not affect the code, except in strings (eg. "Hello World").

### Arrays and Multidimensional Properties in After Effects

In After Effects, you can use arays in expressions, especially for properties with multiple values, such as position (which includes x- and y-coordinates). Arrays allow you to set or adjust multiple dimensions of a property simultaneously.

To set a new value for a property like position use an array: `[value1, value2]`.

To determine the number of dimensions a property has and the values it requires, refer to the table below:

| Dimensions | Property                                                                                                         |
| ---------- | ---------------------------------------------------------------------------------------------------------------- |
| 1          | Rotation (°), Opacity (%)                                                                                        |
| 2          | Scale ([width, height]), Position ([x, y]), Anchor Point ([x, y]), Audio Levels ([left, right])                  |
| 3          | 3D Scale ([width, height, depth]), 3D Position ([x, y, z]), 3D Anchor Point ([x, y, z]), Orientation ([x, y, z]) |
| 4          | Color ([red, green, blue, alpha])                                                                                |

Arrays in After Effects are zero-based, meaning the first element in an array has an index of `0`. Use index numbers to access specific dimensions within an array. For example, with the position property:

- `[0]` refers to the first value (eg. x-coordinate).
- `[1]` refers to the second value (eg. y-coordinate).
- `[2]` refers to the third valye (eg. z-coordinate, for 3D properties).

### Working with Time in Expressions in After Effects

In expressions, time is always measured based on the composition time, not the time within a specific layer. The unit of time is seconds. This allows you to base animations on the progression of time within a composition.

Example: Displaying time in a Text Layer.

You can display the current time in a text layer by following these steps:

- Create a new text layer.
- `Option + click` on the stopwatch for the Source Text Property.
- Add the simple expressions: time.

### Using `seedRandom()` in After Effects

In After Effects, "random" values are not entirely random. The values generated by functions like `random()` follow a predictable pattern because they are based on an algorithm. To gain more control over these "random" values, you can use the `seedRandom()` function. This allows you to maintain the same effect while introducing subtle variations in the generated values.

The function `seedRandom(seed, timeless)` sets a specific seed for the algorthm to generate random values:

- **seed**: A number that determines how the algorithm begins. Different seeds produce different "random" results.
- **timeless**: An optional argument (true/false) that determines whether the generated values should be time-independent. If set to true, the generated values remain constant regardless of the composition's time.

## Looping

The `loopOut()` expression in After Effects automatically repeats an animation based on the keyframes you've set. This eliminates the need to manually copy and paste animations to create a repeated effect.

`loopOut(type = "cycle", numKeyframes = 0)`

**type** (optional): Determines how the animation is repeated. Pissble values are:

- "**cycle**" (default): Repeats the animation from start to finish and starts over.
- "**pingpong**": Repeats the animation by playing it alternately forward and backward.
- "**offset**": Repeats the animation, adding an offset (a shift) with each repetition.
- "**continue**": Continues the motion after the last keyframe, following the direction and speed of the animation.

**numKeyframes** (optional): Specifies the numver of keyframes the loop should consider. By default, it uses all keyframes. This works on most properties except path properties, like those in a shape layer.

### Looping Shape Path Animations

For shape path animations, you need a slightly different expression since `loopOut()` doesn't work directly. Use the following expression instead:  
`valueAtTime(time + key(nulKeys).time)`

### Looping Compositions

You can loop a composition by manipulating the time of a composition layer using the **timeRemap** property. Here's how:

- Select the composition layer in your timeline.
- Go to Layer > Time > Enable Time Remapping.
- Two keyframes will automatically appear on the timeRemap property: one at the start and one at the end of the composition.
- Add the following expression to the timeRemap property: `loopOut()`;
- Now the composition will loop endlessly.

## Expression controls

Expression controls allow you to visualise and easily modify property values. They act as user-friendly interfaces for adjusting expressions, making it simpler to create dynamic and customisable animations. Here are the types of controls available: Andle Control, Checkbox Control, Color Control, Layer Control, Point Control, Slider Control and 3D Point Control.

Expression controls are especially useful for adjusting common values quickly, through the Effects & Presets Panel. You can find them under Effects > Expression Controls.

Although setting up a project with expression control may take a bit more effort initially, it is often essential for working efficiently in complex projects and building dynamix systems that require frequent value adjustments.

Expression controls provide flexibility and ease when managing and customising animations, making them a valuable tool in After Effects.
