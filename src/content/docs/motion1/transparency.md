---
title: Transparency
description: transparency
---

## Transparency

All visual effects are created by combining other visual elements. This allows you to add or remove elements from your footage to create complex visual illusions for the viewer. 

In After Effects, each of these elements is represented by a layer. Layers are positioned one above the other to form a composition. Anything below a layer is no longer visible.

Via Masks, we can cut out certain areas of a layer so that we can see the underlying layer. This is called Masking.

## Masks

A Mask in AE is a path that is used as parameter to modify layer attributes, effects and properties. The most common use of a mask is to adjust the Alpha channel of a layer, which determines the transparency.

A mask belongs to a specific layer. each layer can have several masks. You can draw a mask with geometric shapes such as polygons, ellipses and stars... or you can draw a random path using the pen tool.

The position of a mask (in the stacking order in the timeline panel) affects how it interacts with other masks. You can drag a mask to another position under the Masks property group in the timeline panel (click the arrow next to Layer > Masks).

The opacity of a mask determines its effect on the alpha channel within the mask area. A mask with opacity 100% corresponds to a fully filled area. To invert the mask, click the invert checkbox next to the mask name in the timeline panel.

## Alpha Channel

After Effects summarises colour information into three channels: red (R), green (G) and blue (B). In addition to these channels, an image may contain a fourth channel: an Alpha channel. It contains information about the transparency of the image. RGBA is an RGB image that also contains an alpha channel.

Many file formats have an alpha channel: Photoshop files, TGA, TIFF, EPS, PDF, Illustrator files... AVI and Quicktime can too, but it depends on the codec used to generate and store the images in these containers. After Effects will create alpha channels for the blank sections of an AI, EPS, or PDF file.

## Mask Modes

Blending modes for masks determine how masks within a layer interact. By default, all masks are set to Add, which combines the transparency values of all masks that overlap on the same layer. You can apply a mode to any mask, but you cannot animate this mode. In other words, you can't create keyframes to change the mode over time.

The first mask you create interacts with the alpha channel of the layer. Each additional mask you create affects all other masks present on the layer, taking into account the stacking order in the timeline panel.

- **None**: The mask does not directly affect the alpha channel of the layer. This option is useful if you are just using the path of the mask for an effect such as Stroke or Fill or using it as the basis for a shape path.
- **Add**: The mask is added to the mask above in the stacking order. The effect of the mask is cumulative with the mask above it.
- **Subtract**: The effect of the mask is subtracted from the masks above it.
- **Intersect**: The mask is added to the mask above in the stacking order. In areas where the mask overlaps with the other masks, its influence is cumulative with those above it. In areas where the mask does not overlap, the result is 100% transparent.

## Track Matte

When you want to use a layer as a mask for another layer you can create a track matte. For example: you can use a text layer as a track matte for a video layer to display only video within the characters of the text. The underlying layer (fill layer) get its transparency values from the track matte - either the alpha channel or the brightness of the pixels (luma).

Defining the transparency of a layer based on the luminance of the track matte's pixels is useful if you want to make a track matte of a layer without an alpha channel.

A track matte applies only to the layer immediately below it. To use a track matte over several layers, you must pre-copose those layers and use the track matte on that composition.

A traveling matte is a matte whose position or other transform properties you animate.

## Converting a layer to a track matte

In the timeline panel, drag the layer you want to use as a track matte above the layer you want to use as a fill layer.
If you do not see the `TrkMatte` options in the timeline, you can check them at the very bottom of the panel: `Toggle Switches/Mode`.

Select one of the following options in the `TrkMatte` menu of the fill layer:

- **No Track Matte**: No transparency, the layer above it is like a normal layer.
- **Alpha Matte**: Opaque when the pixel value of the alpha channel is 100%.
- **Alpha Inverted Matte**: Opaque when the pixel value of the alpha channel is 0%.
- **Luma Matte**: Opaque when the pixel value is 100%.
- **Luma Inverted Matte**: Opaque when the luminance of the pixel value is 0%.