(modeling_proj)=

# Projects
Here are some examples made using the tools introduced in this chapter. Feel free to put your own spin on them if you want to try them out, and don't forget to save because you will need them again next chapter.
::::{tab-set}
:::{tab-item} Drink Bottle
1.  Add a **UV Sphere** for the body, and turn down the number of segments for cleaner topology.
```{figure} ../../assets/modeling/project_wb_1.png
:width: 100%
```
2.  Flatten it on the X/Y axis to make the shape easier to grip on.
```{tip}
:class: margin
If you find the shape too boring, feel free to put your own spin on it.
```
```{figure} ../../assets/modeling/project_wb_2.png
:width: 100%
```
3.  Add a `Cylinder` for the neck, and also turn down the number of segments to match the body.
```{figure} ../../assets/modeling/project_wb_3.png
:width: 100%
```
4.  Use a **Boolean** modifier to combine the two and apply, then delete the cylinder object.
```{figure} ../../assets/modeling/project_wb_4.png
:width: 100%
```
5.  Clean up the topology using **Edge Slide** and **Merge**.
```{tip}
:class: margin
- Turn on `Auto Merge Vertices` in the `Options` dropdown menu on the top right corner (or the icon to its left) before `Edge Slide` to make this easier.
- Select the entire mesh by pressing <kbd>A</kbd>, then press <kbd>M</kbd> to bring up the `Merge` menu and choose `By Distance` to clean up some hard-to-spot vertices.
```
```{figure} ../../assets/modeling/project_wb_5.png
:width: 100%
```
6.  Add edge loops and bevel the edges of the neck, then delete the top face.
```{figure} ../../assets/modeling/project_wb_6.png
:width: 100%
```
7.  Make a flat bottom with **Fill**, **Grid Fill**, and **Inset**.
```{figure} ../../assets/modeling/project_wb_7.png
:width: 100%
```
8.  Copy and separate the top ring of faces for later use.
```{figure} ../../assets/modeling/project_wb_8.png
:width: 100%
```
9.  Add **Solidify** and **Subdivide Surface** modifiers to the body.
```{tip}
:class: margin
In the **Solidify** modifier, you can adjust `Edge Data > Crease Inner/Outer` to make edge sharper. Alternatively, apply the modifier and edit the mesh directly.
```
```{figure} ../../assets/modeling/project_wb_9.png
:width: 100%
```
10.  Use **Scale**, **Loop Cut**, **Bevel**, **Fill**, **Grid Fill**, etc. to make the object created in 8 into the shape of a cork.  
```{tip}
Before you edit the mesh, reset its origin by <kbd>Right Mouse Click</kbd> then choose `Set Origin > Origin to Geometry`
```
```{figure} ../../assets/modeling/project_wb_a.png
:width: 100%
```
11.  Adjust the position and size of the objects and apply **Shade Auto Smooth**. 
```{figure} ../../assets/modeling/project_wb_overview.png
:width: 100%
```

:::

:::{tab-item} Chess Piece
In 3D modeling, you will often find multiple solutions to achieve the same goal. Here we are going to make a pawn piece in 3 different ways.
```{note}
:class: margin
The referece used in this project is obtained from [Pixabay](https://pixabay.com/illustrations/chess-black-and-white-pieces-3413429/).
```

1. Add the reference image and adjust its position.
```{figure} ../../assets/modeling/project_pawn_ref.png
:width: 100%
```

````{admonition} Starting with a Mesh Circle
:class: seealso
2. Add a Circle and use **Extrude** and **Scale** to trace the reference.
```{figure} ../../assets/modeling/project_pawn_circle_1.gif
:width: 100%
```

3. Fill the top and bottom.
```{figure} ../../assets/modeling/project_pawn_circle_2.png
:width: 100%
```

4. Add a **Subdivision Surface** modifier, and make adjustments to finalize the model.
```{figure} ../../assets/modeling/project_pawn_circle_3.png
:width: 100%
```



````
````{admonition} Starting with a Cylinder
:class: seealso
2. Add a Cylinder and use **Scale** to fit the size of the reference.
```{figure} ../../assets/modeling/project_pawn_cyliner_1.png
:width: 100%
```

3. Use **Loop Cut**, **Scale**, **Edge Slide**, **Move**, etc. to make the general shape.
```{figure} ../../assets/modeling/project_pawn_cyliner_2.png
:width: 100%
```

4. Add a **Subdivision Surface** modifier, and make adjustments to finalize the model.
```{figure} ../../assets/modeling/project_pawn_cyliner_3.png
:width: 100%
```


````

````{admonition} Using Curve
:class: seealso
2. Add a curve (`Bezier` in this example) and edit it to trace half of the reference image.
```{figure} ../../assets/modeling/project_pawn_curve_1.png
:width: 100%
```

3. Add a **Screw** modifier and tweak the options to make it look better. 
```{figure} ../../assets/modeling/project_pawn_curve_2.png
:width: 100%
```


````

:::

:::{tab-item} "Barrel Roll"
1. Use your imagination and put together a low-poly space fighter or any cool-looking flying object. Make the main body the parent of all other parts.
```{figure} ../../assets/modeling/project_br_1.png
:width: 100%
```

2. Add a curve and edit it by making/adjusting control points/handles to construct a flying path. 
```{figure} ../../assets/modeling/project_br_2.png
:width: 100%
```

3. Add a **Follow Path** constraint to the main body, and tweak the properties to make the animation look right.
```{figure} ../../assets/modeling/project_br_3.gif
:width: 100%
```

:::

::::
