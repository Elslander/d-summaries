---
title: Shape Layers
description: shape layers
---

## Adding Shape Layers

Shape layers are used to create and contain objects, known as shapes. A typical shape is made up of a path, stroke, and fill. You can create shape layers using the shape tools or the pen tool from the toolbar. Be sure to deselect any layers, or you might create a mask instead of a shape.

Here are some common ways to create a shape or shape layer:

- Draw a path using the shape tools or pen tool.
- Convert a text layer to shapes using the "Create Shapes from Text" command.
- Convert a mask path to a shape path.
- Paste a copied path from another layer or from Adove Illustrator or Photoshop.
- Create a new, empty shape layer: go to `Layer > New > Shape Layer`.

We will focus on the last method for creating shape layers.

### Choosing Shapes for a New Shape Layer

Once you've created a new, empty shape layer, you'll need to define the shapes it contains. You can do this by clicking the "Add" button located on the right of the layer panel.

### Importance of Shape Layer Order

The order of elements in a shape layer is crucial, especially when working with repeaters, multiple shapes, or applying other Shape Layer effects. To manage this effectively, it's recommended to create a new group for each shape. For example to create a simple square:

1. Create a new group.
2. Add a rectangle path.
3. Apply a fill color.

Shape layers have their own transform properties, similar to other layer. Wgen you animate the position of the shape layern, all shapes inside it move together. However, by using groups, you can animate each shape individually, as each group has its own transform properties - this is a key advantage of using groups.

You can apply the same steps to create other shapes like ellipses, polystars, or custom paths, each offering unique shaping options.

### Shape Layer Effects (operators)

In addition to creating shapes, the Shape Layer menu also offers various effects (called operators), such as: *Merge Paths*, *Offset Paths*, *Pucker & Bloat*, *Repeater*, *Rounded Corners*, *Trim Paths*, *Twist*, *Wiggle Paths*, *Wiggle Transform*, *Zig Zag*.

We will explore some of these in more detail.

### Centering the Anchor Point

To automatically center the anchor point for every new shape, adjust your preferences in After Effects by going to Preferences > General > Center Anchor in New Shape Layer.

## Shape Operators

Along with shapes and fills, you can apply effects to selected shapes. Keep in mind that the order of operations is important - effects are often applied only to the shape or element above them in the layer stack.

### Merge Paths

Similar to Illustrator's pathfinder panel, Merge Paths allows you to combine two or more shapes:

- **Merge**: Treats all shapes as one; the stroke remains intact.
- **Add**: Combines multiple shapes into one new shape.
- **Subtract**: Removes underlying shapes from the top shape.
- **Intersect**: Keeps only the overlapping section of all shapes.
- **Exclude Intersections**: Keeps everything except the common intersection of the top shapes.

### Trim Paths

Trim Paths is a useful operation for trimming a path to create effects like write-on animations. The start, end, and offset properties determine how the shape appears. This effect is best used with strokes, rather than filled areas.

When using the Trip PAth effect, if you set "Trim Multiple Shapes" to "Individually" (instead of the default "Simultaneously"), each shape within the shape Layer will be trimmed one after the other.

### Repeater

A path operation used to generate multiple copies of a shape withing a shape layer, applying specific transformations to each copy. The repeater duplicates all paths, strokes, and fills athat are above the effect or withing the same group.

You can apply multiple repeaters in the same group, allowing for complex patters. For example, one repeater can be used to repeat shapes horizontally, while another can repeat them vertically, making it easy to create a grid of shapes.

The *Composite* option controls wether each copy is rendered in front of or behind the previous one. Repeaters are a powerful tool for creating intricate animations within a single shape layer.