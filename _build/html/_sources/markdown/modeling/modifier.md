(modifier)=
# Modifier
Modifiers are functions that change an object's geometry without affecting its underlying mesh data. They let you easily apply various effects and reverse them as you need.

(modifier:add)=
## Adding modifier
Modifiers are properties of an object, to add one, make sure you are in object mode, then select an eligible object and choose `Modifier Properties > Add Modifier` in the properties area to bring up the dropdown menu. There are 4 categories of modifiers, `Modify`, `Generate`, `Deform`, and `Physics`, we will focus on the `Generate` type in this tutorial. <kbd>Left Mouse Click</kbd> on the modifier you want to add, then you can see the effect. One object can have multiple modifiers, and they will be applied from top to bottom. To change the order of the modifiers, hold <kbd>Left Mouse Button</kbd> on the top right corner of a modifier, then drag it up or down. If you want to delete a modifier, <kbd>Left Mouse Click</kbd> on the cross near the top right.
```{figure} ../../assets/modeling/add_mod.png

```

```{tip}
:class: margin
Modifiers apply before object transfomation, if the object has been trasformed (especially scaled), some modifiers may not behave as expected. To avoid that, ou can select an object and press <kbd>Ctrl + A</kbd> to bring up the `Apply` menu and apply object transformation to mesh data.
```

## Visibility
On the right of the name of the modifier, there are icons (depending on the type of the modifier) that let you change how the modifier will affect the view. Try them out in both object and edit mode.
```{figure} ../../assets/modeling/visibility.png

```

## Applying a modifier
To make the effect of a modifier permanent(apply it to the mesh data), move the cursor on the modifier interface and press <kbd>Ctrl + A</kbd>,  or <kbd>Left Mouse Click</kbd> on the downward arrow to the left of the cross and use the menu to `Apply` the effect.

```{figure} ../../assets/modeling/apply_mod.png

```

(modifier:common)=
## Commonly used modifiers

::::{tab-set}
:::{tab-item} Subdivision Surface

The **Subdivision Surface** modifier(commonly known as "Subsurf") is probably the one you are going to use the most. The default option, `Catmull-Clark` smooths out the mesh and increases the polygon count, and `Simple` only divides the faces (like **Subdivide** in edit mode).

```{tip}
:class: margin
Since this modifier is used so often, Blender has shortcut for adding it by default: <kbd>Ctrl + 1</kbd>, <kbd>Ctrl + 2</kbd>... <kbd>Ctrl + 5</kbd> to add it with 1 to 5 level.
```

```{figure} ../../assets/modeling/subsurf.gif
:width: 100%
```

Because a modifier does not change the mesh, you can easily adjust the shape.
```{figure} ../../assets/modeling/subsurf_edit.gif
:width: 100%
```


To preserve sharp edges, you can bevel the edges, add support loops, or use **Edge Crease**. To bevel the edges, use the **Bevel** tool explained in the [Mesh Modeling](mesh) section or the **Bevel** modifier in the other tab (you need to move it on top of this modifier so it applies first). Support loops are edge loops close to the edge you want to keep sharp, use **Loop Cut** and **Inset** tools to add them. Last but not least, **Edge Crease** is a property of an edge, select the edge/edges you want to keep sharp and adjust `Crease`/`Mean Crease` in the sidebar.

```{figure} ../../assets/modeling/subsurf_sharp_edge.gif
:width: 100%
```
:::

:::{tab-item} Bevel
The **Bevel** modifier allows you to bevel all the edges or vertices (corners) of a mesh at once. By default it affects all edges, and you can adjust `Amount` and `Segements` to fit your needs. To bevel the corners, <kbd>Left Mouse Click</kbd> the `Vertices` tab on the top. If you find shading on the faces looks weird, try turning on `Shading > Harden Normals`.

```{figure} ../../assets/modeling/bevel_mod.gif
:width: 100%
```

:::

:::{tab-item} Array
The **Array** modifier makes copies of an object and arranges them in different ways. Adjust `Count` to change the number of copies and `Relative Offset > Factor X/Y/Z` for the offsets on the three local axes.

```{figure} ../../assets/modeling/array_1.gif
:width: 100%
```

To arrange the copies in more interesting ways, you can adjust `Object offset`. The location/rotation of the copies will be affected by the object specified in `Object offset > object`.

```{tip}
:class: margin
It is common to use an **Empty**, a type of object with no geometry, to control the effects. You can add one to your scene in the `Add` menu.
```

```{figure} ../../assets/modeling/array_obj.gif
:width: 100%
```

:::

:::{tab-item} Boolean
```{tip}
:class: margin
Beware that this modifier is prone to creating bad topology, especially when the meshes get more complex.
```
The **Boolean** modifier is like logical operators in programming but for 3D meshes. Set the other object for the operation in `Object`, and choose `Intersect`, `Union`, or `Difference` for **AND**, **OR**, and **NOT** effect. 
```{figure} ../../assets/modeling/boolean.gif
:width: 100%
```

:::

:::{tab-item} Mirror
If you are modeling something symmetrical, the **Mirror** modifier can save you a lot of work. You can control on which local axes this effect will be applied by `Axis X/Y/Z`, and they are not mutually exclusive.

```{figure} ../../assets/modeling/mirror.gif
:width: 100%
```

:::

:::{tab-item} Solidify
The **Solidify** modifier adds depth to all faces. Change `Thickness` to tweak the amount of depth added and `Offset` to influence on which side of the face this effect applies. Ticking `Even Thickness` may help to make the resulting mesh look better.
```{tip}
:class: margin
The `Offset` is relative to face normals.
```
```{figure} ../../assets/modeling/solidify.gif
:width: 100%
```

:::

:::{tab-item} Screw
The **Screw** modifier takes an object as a profile and creates a helix or rotationally symmetric shape, depending on the offset. 
```{figure} ../../assets/modeling/screw.gif
:width: 100%
```
It also works on curve objects.
```{figure} ../../assets/modeling/screw_curve.gif
:width: 100%
```
:::

::::
