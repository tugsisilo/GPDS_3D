(shader_node_tree)=

# More about Shader Nodes
The last section explained the standard makeup of a realistic-looking material, but it is far from the only way. You probably noticed that there are a lot more shader nodes than the ones we used, and with their power combined, the only limit is your imagination.

## Socket Types
```{tip}
:class: margin
The **Fac(facor)** socket outputs/expects input float values between 0 and 1.
```
The color of the sockets on the nodes indicates the type of data, here are the common ones:
- <span style="color:#0FFF50">Light green</span>: Shader
- <span style="color:#008000">Dark green</span> : Integer
- <span style="color:#808080">Grey</span>: Float
- <span style="color:#FFFF00">Yellow</span>: Color
- <span style="color:#FFC0CB">Pink</span>: Boolean
- <span style="color:#BF40BF">Purple</span>: Vector
- <span style="color:#FFA500">Orange</span>: Object

Some types can be automatically converted to another when the sockets are connected, and the noodle will have a gradient between the two colors. When the conversion is not possible, the noodle will appear red.

## Layout
When you have dozens of nodes in your node tree, it is important to keep them well organized. The **Frame** is a useful tool to remind yourself what all these nodes do. To make a new frame, select the nodes you want to be part of it and press <kbd>Ctrl + J</kbd> or <kbd>Right Mouse Click</kbd> to bring up `Node Context Menu` and choose `Join in New Frame`. You can give the frame a `Label` via `Node > label` in the `Sidebar`. To add new nodes to the frame, simply drag them into the frame; to remove, press <kbd>Alt + P</kbd> or choose `Remove from Frame` in the `Node Context Menu`.
```{tip}
:class: margin
You can give label to nodes in the same way.
```
```{figure} ../../assets/material/node_frame.gif
:width: 100%
```


## Group
In programming, we write custom functions to avoid code repetition. The **Node Groups** can help us with that problem in node trees. Select the nodes you want to group up, then press <kbd>Ctrl + G</kbd> or <kbd>Right Mouse Click</kbd> to bring up `Node Context Menu` and choose `Make Group`. Inside the node group, you can link input sockets to the hollowed circle on the `Group Input` to add new inputs to the Group, or output ones to the `Group Output` to make new outputs. To change the names and types of the sockets, open the sidebar and switch to the `Group` tab.

Press <kbd>Tab</kbd> to return to the node tree, and you can <kbd>Left Mouse Click</kbd> the symbol on its top right or select and press <kbd>Tab</kbd> to get inside the node group again. Linking a node group is the same as any regular node. After you have made a node group, you can add a copy through `Add > Group > {Group Name}`.
```{tip}
:class: margin
Editing a node group will change all its instances because they share the underlying data. To avoid that behavior, <kbd>Left Mouse Click</kbd> the number to the right of the name of the node group and it will creat a copy of the original group in the data.
```
```{figure} ../../assets/material/node_group.gif
:width: 100%
```

## Use Add-ons
One advantage of Blender is that it has great community support, and you can find all kinds of **Add-ons** to enhance its functionality. When it comes to nodes, the **Node Wrangler** is a very popular one and you already have it in your installation. This add-on provides various tools to make node editing easier. Open `Blender preferences` window using `Edit > Preferences...`, in the `Add-ons` tab, you can find the add-on in the list or search it by name, then tick the box to enable.
```{tip}
:class: margin
- One useful functionality of this add-on is to connect the output of a node to the `Surface` socket of the `Material Output` node by  <kbd>Ctrl + Shift + Left Mouse Click</kbd>, it allows you to quickly check how the output of a node looks.
- Apart from the ones that come with Blender, you can find much more free and paid add-ons online.
```
```{figure} ../../assets/material/addon.png

```

## More Nodes
::::{tab-set}
:::{tab-item} Input

````{card} Ambient Occlusion
If you are a PC gamer, the word **Ambient Occlusion** may sound familiar. Ambient occlusion is a technique of simulating shadows in the nooks and crannies which are often not calculated in shadow maps. 
```{figure} ../../assets/material/node_ao.png
:width: 100%
```
You can use it for that purpose, or use the `AO` output as a mask for other effects.
```{figure} ../../assets/material/node_ao_ex.png
:width: 100%
```
````

````{card} Frensnel
The observed reflectiveness of a material is dependent on the viewing angle, and it is called the **Frensnel** effect. The Fresnel node gives you a factor indicating which part of the material should me more reflective.
```{figure} ../../assets/material/node_fensnel.png
:width: 100%
```
It is often used along with **Mix Shader**. This example shows a mixture of a matte blue material and a glossy red one.
```{figure} ../../assets/material/node_fensnel_mix.png
:width: 100%
```
````

<!-- 
````{card} Light Path

```{figure} ../../assets/material/pbsdf_subsurface.png

```
````
 -->

````{card} UV Map
Yes, you can use the `UV` output of the texture coordinate node, but if the object has multiple UV maps, it only use the active one. The **UV Map** node let you choose which UV map you want to use.
```{figure} ../../assets/material/node_UV.gif
:width: 100%
```
````

````{card} Value
The **Value** node is very simple: it stores and outputs 1 value. It is useful when you want to link multiple input values together.
```{figure} ../../assets/material/node_value.gif
:width: 100%
```
````


:::


:::{tab-item} Output
````{card} Material Output
Every material needs a **Material Output** node to work. The `Surface` and the `Volume` socket are for their respective shaders, and `Displacement` is for the displacement effect introduced in the last section. It also let you make different outputs for **EEVEE** and **Cycles** render engines.
```{figure} ../../assets/material/node_mat_output.png
:width: 100%
```
````


:::


:::{tab-item} Shader
Most of the nodes here can be seen as components of the principled BSDF shader, and they give you more freedom to create new materials.
````{card} Mix Shader
Real-life materials are usually not uniform, and different part has different properties. The **Mix Shader** node allows you to combine two shaders together with their arrangement defined by the `Fac` input. With the help of Node Wrangler, this node can also be created by holding <kbd>Ctrl + Shift + Right Mouse Button</kbd> and dragging the cursor from one shader to another.
```{figure} ../../assets/material/node_mix_shader.png
:width: 100%
```
````


````{card} Volume Absorption
To create colored translucent material like tinted glass, you will need the **Volume Absorption** node. Be sure to connect its output to the `Volume` input socket of the `Material Output` node.
```{tip}

Switch to **Cycles** render engine for better results.
```
```{figure} ../../assets/material/node_vol_absorb.png
:width: 100%
```
It is often combined with a surface material.
```{figure} ../../assets/material/node_vol_absorb_combo.png
:width: 100%
```

````

````{card} Volume Scatter
Adding some fog to your scene can make it look less empty, and the **Volume Scatter** node helps you to create such material. In this example, such material is applied to a cube, and another object with an emissive material is put insde the cube.
```{tip}

Switch to **Cycles** render engine for better results.
```
```{figure} ../../assets/material/node_vol_scatter.png
:width: 100%
```
````


:::


:::{tab-item} Texture

````{card} Brick Texture
The **Brick Texture** makes procedually generated brick wall textures, or other tiled textures if you use it in more creative ways. The `Color` socket outputs the texture, and `Fac`gives you a factor where the brick parts are 0s and mortar 1s.
```{figure} ../../assets/material/node_brick_tex.png
:width: 100%
```
```{figure} ../../assets/material/node_brick_fac.png
:width: 100%
```
````


````{card} Gradient Texture
**Gradient Texture** can help you make a blend or fade in/out effect. 
```{figure} ../../assets/material/node_grad_tex.gif
:width: 100%
```
````


````{card} Magic Texture
The **Magic Texture** may look weird, but it is useful for generating repeating patterns. If you look at its R(ed)/G(reen)/B(lue) channel separately using the **Separate Color** node, the simpler underlying patterns will reveal themselves.
```{figure} ../../assets/material/node_magic_tex.gif
:width: 100%
```
````


````{card} Musgrave Texture
The **Musgrave Texture** is based on **Perlin noise**, and it gives you more control compared to the **Noise Texture** node. 
```{figure} ../../assets/material/node_musgrave.png
:width: 100%
```
It is good at mimicking organic surface and creating terrain. Unlike the more common `Fac` output, the `Height` output is not limited to the range of 0 to 1, and you can see the effect when using it for `Displacement`. When the number of dimension is set to `4D`, you can use `W` as a random seed or for animation.
```{figure} ../../assets/material/node_musgrave_terrain.png
:width: 100%
```
```{figure} ../../assets/material/node_musgrave_anim.gif
:width: 100%
```

````

````{card} Noise Texture
**Noise Texture** generates a pattern based on **Perlin noise**. The `Fac` output pattern is the same as the red channel in the `Color` output.
```{figure} ../../assets/material/node_noise_tex.png
:width: 100%
```
You can use it to add some flavor to your material, or combine it with other textures to create interesting effets.

```{figure} ../../assets/material/node_noise_wave.png
:width: 100%
```
```{figure} ../../assets/material/node_noise_rough.png
:width: 100%
```
````

````{card} Voronoi Texture
The **Voronoi Texture** is based on **Worley noise**, which is generated by evaluating distance to random points in space. Changing the defination of distance gives you different outputs. When the number of dimension is set to `4D`, you can use `W` as a random seed or for animation.
```{figure} ../../assets/material/node_voronoi_tex.png
:width: 100%
```
````

````{card} Wave Texture
The **Wave Texture** gives you bands and rings. Putting it on a 3D object will give you a better understanding on how it works.
```{figure} ../../assets/material/node_wave_tex.png
:width: 100%
```
Combine it with other texture nodes to create interesting effects.
```{figure} ../../assets/material/node_wave_anim.gif
:width: 100%
```
````

:::

:::{tab-item} Vector
````{card} Bump
The **Bump** node takes a `Height(float)` input and outputs a normal map.
```{figure} ../../assets/material/node_bump.png
:width: 100%
```
````


:::

:::{tab-item} Color
````{card} Mix Color
Not to be confused with the **Mix Shader** node in `Shader`, the **Mix Color** node offers various ways to mix two color inputs depeneding on the `Blend Mode`. With the help of Node Wrangler, this node can also be created by holding <kbd>Ctrl + Shift + Right Mouse Button</kbd> and dragging the cursor from one node with `Color` output socket to another.
```{tip}
The **Mix** node in `Converter` is actually the same as this node.
```
```{figure} ../../assets/material/node_mix_color.png
:width: 100%
```
````


:::




:::{tab-item} Converter

````{card} Blackbody
The **Blackbody** node converts `Temperature(float)` to a `Color` based on blackbody radiation.
```{figure} ../../assets/material/node_blackbody.gif
:width: 100%
```
````


````{card} Color Ramp

**Color Ramp** maps values to colors. You can <kbd>Left Mouse Click</kbd> `+` to add a new `Color Stop` and `-` to delete. To change the color, select a `Color Stop` then <kbd>Left Mouse Click</kbd> the color bar.
```{tip}
You can use this node to map values too.
```
```{figure} ../../assets/material/node_coloramp.png
:width: 100%
```
It can be used as a simple tool to adjust contrast.
```{figure} ../../assets/material/node_coloramp_contst.gif
:width: 100%
```
You can also use it along with the **Shader To RGB** node to get a cel/toon shading effect.
```{figure} ../../assets/material/node_coloramp_toon.png
:width: 100%
```


````

````{card} Map Range
The **Map Range** node map values from one range to another.
```{figure} ../../assets/material/node_map_range.gif
:width: 100%
```
````

````{card} Separate/Combine XYZ
The **Separate XYZ** and **Combine XYZ** nodes allow you to separate/combine a vector into/from 3 float values. They are very useful when you are trying to read/manipulate coordinates on one axis.
```{figure} ../../assets/material/node_sep_comb_xyz.gif
:width: 100%
```
````

````{card} Shader To RGB (EEVEE Only)
The **Shader To RGB** node is used for stylized rendering, it allows you to manipulate the output of a shader. See **Color Ramp** for the example.
````

````{card} Math/Vector Math
The **Math** and **Vector Math** nodes allow you to perform mathmatical operations. You can use them to adjust values, draw shapes, etc.
```{figure} ../../assets/material/node_math.png
:width: 100%
```
````



````{card} Wavelength
The **Wavelength** node convert a wavelength (float) to a color, it will produce pure black if the value is out of the range of visible light.
```{figure} ../../assets/material/node_wavelength.gif
:width: 100%
```
````

:::

::::