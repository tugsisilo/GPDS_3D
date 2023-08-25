# More about Add-ons
Here are some more details on the add-ons used in this tutorial.


## Node Wrangler
Apart from the usages mentioned in the previous chapters, **Node Wrangler** has more tricks under its sleeve.
::::{tab-set}
:::{tab-item} Swap Inputs
If a node has two input links, pressing <kbd>Alt + S</kbd> will swap them around. If only one input link exists, pressing <kbd>Alt + S</kbd> will cycle the link through the input sockets.
```{figure} ../../assets/extra/nw_input_swap.gif
:width: 100%
``` 
:::

:::{tab-item} Switch Node Type
You can press <kbd>Shift + S</kbd> to switch the type of selected node.
```{figure} ../../assets/extra/nw_type_swap.gif
:width: 100%
``` 
:::

:::{tab-item} Align Nodes
Select the nodes you want to align, then press <kbd>Shift + =</kbd>.
```{figure} ../../assets/extra/nw_node_align.gif
:width: 100%
``` 
:::

:::{tab-item} Add Texture Setup
Pressing <kbd>Ctrl + T</kbd> automatically adds a commonly used setup to a shader, texture, or background node.
```{figure} ../../assets/extra/nw_setup_add.gif
:width: 100%
``` 
:::

:::{tab-item} Delete Unused Nodes
After experimenting with different node setups, you may have extra unconnected nodes lying around. To delete all of them, press <kbd>Alt + X</kbd>.
```{figure} ../../assets/extra/nw_del_nodes.gif
:width: 100%
``` 
:::

::::

## Extra Objects
The **Extra Objects** add-on gives us a series of customizable primitive mesh objects, here are some examples.
::::{tab-set}
:::{tab-item} Teapot
`Mesh > Extra > Teapot+` adds a teapot or a tea spoon.
```{tip}
:class: margin
The teapot serves the same purpose as Suzanne in some other 3D softwares.
```
```{figure} ../../assets/extra/eo_teapot.gif
:width: 100%
``` 

:::

:::{tab-item} Gem
`Mesh > Diamonds` offers 3 different customizable gem shapes.
```{figure} ../../assets/extra/eo_gem.png
:width: 100%
``` 

:::

:::{tab-item} Regular Solid
`Mesh > Math Function > Regular Solid` can create basic mathmatical shapes. Choose a `Source` and tweak it to your liking, or pick one from the `Presets`.
```{figure} ../../assets/extra/eo_soild.gif
:width: 100%
``` 

:::

:::{tab-item} Math Surfaces
`Mesh > Math Function > Z Math Surface/ XYZ Math Surface` makes 3D presentations of mathmatical functions. 
```{tip}
:class: margin
These are mesh objects, not curve.
```
```{figure} ../../assets/extra/eo_math_surf.png
:width: 100%
``` 

:::



::::


## Loop Tools

The **Loop Tools** add-on offers extra tools for mesh editing, you can find them in the `Edit` tab on the sidebar while in edit mode. Check the following examples and try them out yourself.
::::{tab-set}

:::{tab-item} Circle
The **Circle** tool moves the selected vertices to form a circle.
```{figure} ../../assets/extra/lt_circle.gif
:width: 100%
``` 
:::

:::{tab-item} Relax
The **Relax** tool makes the surface smoother.
```{figure} ../../assets/extra/lt_relax.gif
:width: 100%
``` 
:::

:::{tab-item} Space
The **Space** tool tries to space out the vertices more evenly.
```{figure} ../../assets/extra/lt_space.gif
:width: 100%
``` 
:::


::::