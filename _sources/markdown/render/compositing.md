(Compositing)= 
# Compositing
Compositing allows you to combine multiple images and add post-processing effects. In this section, we focus on some simple effects you can see in real-time.

## Enable Compositor
Switch one area to the `Compositor` type, tick `Use Nodes` and now the compositor is enabled. The compositor always affects the rendered image, but if you want to see it in real-time, switch the `Viewport Shading` to `Material Preview` or `Rendered`, then <kbd>Left Mouse Click</kbd> {octicon}`chevron-down` on the right and choose `Always` under `Compositor`, or `Camara` if you only want to see the effects in camera view. Adding and connecting compositor nodes are the same as shader nodes, see the [previous chapter](PBR_mat) for details.
```{tip} 
:class: margin
Some nodes are not supported in the viewport.
```
```{figure} ../../assets/render/compositor_enable.gif
:width: 100%
```

## Nodes
::::{tab-set}
:::{tab-item} Anti-Aliasing
The `Filter > Anti-Aliasing` node makes jagged edges smoother, especially useful when the rendering sample count is low.
```{tip} 
:class: margin
- The options such as FXAA, TAA, SMAA you see in video games are all different anti-aliasing algorithms.
- Unlike a softening filter, anti-aliasing detects edges (through contrast, depth buffer, etc.) and the effect is only applied there.
```
```{figure} ../../assets/render/aa_before.png
```
```{figure} ../../assets/render/aa_after.png
```
:::

:::{tab-item} Denoise
```{tip} 
:class: margin
Select a node and press <kbd>M</kbd> to mute/disable the node, press again to undo it.
```
The `Filter > Denoise` node provides a more customizable denoiser.
```{figure} ../../assets/render/denoise_node.gif
:width: 100%
```
:::

:::{tab-item} Blur
The `Filter > Blur` node can blur the image in various ways. The following example uses `Gaussian` blur.
```{figure} ../../assets/render/blur_gaussian.gif
:width: 100%
```
:::

:::{tab-item} Glare
The `Filter > Glare` node reproduces imaging artifacts around bright spots. This example uses the `Fog Glow` type, creating a bloom effect.
```{figure} ../../assets/render/glare_bloom.gif
:width: 100%
```

:::

:::{tab-item} Filter
The `Filter > Filter` provides various image filters, such as softening, sharpening, etc. This example uses the `Sobel` type, which creates a highlighted edge.
```{figure} ../../assets/render/filter_sobel.gif
:width: 100%
```

:::

:::{tab-item} Lens Distortion
The `Distort > Lens Distortion` node simulates imperfections created by real-world lenses. `Distort` distorts the shapes and `Dispersion` creates a chromatic aberration effect (also known as color fringing).
```{figure} ../../assets/render/lens_distortion.gif
:width: 100%
```
:::

::::