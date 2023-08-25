(object)=

# Object

When you open Blender or make a new file, you will see things already in the viewport: a cube, a point light, and a camera. These are all
**Objects** in Blender, therefore they have some common properties. To interact with objects in the 3D viewport, check the header and make sure it is in `Object Mode`.

## Adding an object

Click `Add` on the header or press <kbd>Ctrl + A</kbd> to bring up the Add menu, then choose the object you want to add to the scene. The object will appear at the position of the **3D Cursor**, which is the thing you can see in the viewport that looks like a life preserver but is way too thin to save anybody. To move it, hold <kbd>Shift</kbd> and <kbd>Right Mouse Click</kbd>, or press <kbd>Shift + S</kbd> and choose the option you want on the radial menu.

```{figure} ../../assets/modeling/add.gif

```

## Outliner and Collection

The **Outliner** area is on the top right by default, and it lists all the objects in the scene. <kbd>Left Mouse Click</kbd> on the little triangle reveals the data linked to the object. **Collection** is a tool to organize your objects, you can make new ones by <kbd>Right Mouse Click</kbd> and choosing `New Collection` in the menu. To move an object into the new collection, hold <kbd>Left Mouse Button</kbd> on it and drag it there.

```{figure} ../../assets/modeling/outliner.gif

```

## Toolbar

The **Toolbar** contains tools represented as icons on the left part of an area, its contents depend on the type of the area and the mode the area is in. <kbd>Left Mouse Click</kbd> to select a tool, and for the tools with a small triangle at the bottom right corner, you can hold <kbd>Left Mouse Button</kbd> to choose a variant.

```{figure} ../../assets/modeling/toolbar.gif

```

## Origin

Every object in the 3D viewport has an **Origin** point, and the point is displayed as a small orange circle when the object is selected. The origin decides the position of the object, and object rotation and scaling are calculated with respect to this point.

## Global and Local axes

The red, green, and blue (not always shown by default) lines displayed on the 3D viewport represent X, Y, and Z axis respectively. This is for the **Global** space we often operate in. Besides that, all objects have their own **Local** axes, and you can check that by ticking `Object Properties > Viewport Display > Show axes` in the **Properties** area (bottom right by default).

```{figure} ../../assets/modeling/global_local.PNG

```

## Basic tools

::::{tab-set}
:::{tab-item} Selection
By default, <kbd>Left Mouse Click</kbd> selects an object (in the viewport or the outliner), and holding it down gives you **Box Selection**. The selected object should have a bright orange border. To select multiple objects, hold down <kbd>Shift</kbd> and <kbd>Left Mouse Click</kbd>. The last selected object will be the **Active Object**, with a bright orange border, and the others with dark orange ones. Blender offers various tools for selection, you can access them using the `Select` menu in the header.

:::

:::{tab-item} Move
Press <kbd>G</kbd> or use the move tool in the toolbar to move an object. Like most operations in Blender, <kbd>Left Mouse Click</kbd> to confirm and <kbd>Right Mouse Click</kbd> to cancel the change. To snap the object to the grid, <kbd>Left Mouse Click</kbd> the magnet icon on the header to turn it on, or hold <kbd>Ctrl</kbd> to use it temporarily. If you want the object to move strictly on on axis
Last but not least, drag out the menu on the right, and in `Item` tab

<!-- Snap, On-axis(global and local), precision -->

```{figure} ../../assets/modeling/move.gif

```

:::
:::{tab-item} Rotate
Content...

<!-- Double R -->

```{figure} ../../assets/modeling/rotate.gif

```

<!-- pivot point -->

```{figure} ../../assets/modeling/rotate_pivot.gif

```

:::
:::{tab-item} Scale
Content...

<!-- Blender unit, On-axis, linked, precision -->

```{figure} ../../assets/modeling/Scale.gif

```

:::

:::{tab-item} Hide
Content...

<!-- local view / -->

```{figure} ../../assets/modeling/hide.gif

```

:::

:::{tab-item} Join

```{figure} ../../assets/modeling/join.gif

```

:::

:::{tab-item} Parent
In Blender, the concept of Parenting is like ducklings following their mom, not the scary and stressful kind.

```{figure} ../../assets/modeling/parent.gif

```

:::

::::
