(mesh_editing)=

# Mesh Modeling

**Mesh Modeling** is the most common way to make 3D models for all kinds of things. Before we dive into how we do it, let's go through some basics first.

## Edit Mode

**Edit mode** is the 3D viewport interaction mode in which we do all the mesh modeling. Select a mesh object(like the cube you already have), use the drop-down menu on the left side of the header or press <kbd>Tab</kbd> to enter edit mode. You can also select multiple mesh objects to edit them at the same time. Once in edit mode, the toolbar offers a different list of tools, and the header also partially changes compared to object mode.

```{figure} ../../assets/modeling/edit_mode.png
:width: 100%
```

## Vertex, Edge, and Face

All mesh consists of **Vertices**, **Edges**, and **Faces**. Vertices, represented by small squares in **Vertex Select** mode, are points in space without any volume. Edges are lines created by connecting two Vertices, and faces are surfaces/polygons defined by the edges surrounding them. To modify vertices/edges/faces, you can switch to the desired `Select Mode`, by <kbd>Left Mouse Click</kbd> on their respective icons on the right of the object interactive mode selection, or pressing<kbd>1</kbd>,<kbd>2</kbd>, and <kbd>3</kbd>(not to be confused with <kbd>Numpad 1</kbd>, <kbd>Numpad 2</kbd>, and <kbd>Numpad 3</kbd>)

```{tip}
:class: margin
- If this is the first time you ever enter edit mode, The `Select Mode` should be `Vertex Select`.
- When you switch the `Select Mode` from face select to `Edge/Vertex Select`, the edges/vertices associated with the chosen face will remain selected. This also applys to changing from `Edge Select` to `Vertex Select`.
```

```{figure} ../../assets/modeling/mesh_select_mode.gif
:width: 100%
```

An important property of a face is its **Normal**. If you still remember your math, the normal vector is the vector perpendicular to a surface, and this is also the case in 3D modeling. It is used to determine the direction a face is pointing and is crucial to shading.
````{tip}
:class: margin
- If you just want know whether you are looking at the front or back side of the faces, open the `Viewport Overlay` menu and tick `Geometry > Face Orientation`. The front of a face will be blue and the back will be red.
```{figure} ../../assets/modeling/face_orientation.gif
:width: 100%
```
- This is Suzanne the Monkey, you can add her to your scene in `Add > Mesh > Monkey`.
```````
```{figure} ../../assets/modeling/normal.png

```
(face_types)=
## Tri, Quad, N-Gon, and Pole

To make nice-looking meshes, there are some concepts you need to remember, and an important one is the type of faces you will be making. A face with 3 edges is called a **Tri(triangle)** (like face 5 and 6 in the image), 4 called a **Quad(quadrilateral)**(like face 7), and 5 or more an **N-Gon** (like face 23). Generally speaking, quads are considered the most desirable because they work well with all the tools in 3D modeling software; tris does not work with certain tools, like loop cut(you will see it soon); N-Gons should be avoided because they are prone to producing unwanted results.
```{tip}
:class: margin
To see the indices, you need to turn on `Developer Extra` in `Edit > Preferences > Interface > Display`, then open `Viewport Overlay` dropdown menu on the right side of the header (to the left of `Viewport Shading` toggles) and tick `Developer > indices`.
```
```{figure} ../../assets/modeling/tri_quad_ngon.png

```
```{tip}
:class: margin
You can find out more about topology in 3D modeling [here](https://topologyguides.com/).
```
Another important concept is the **Pole**, which are vertices connected to three, five, or more edges. They may cause issues when subdividing or deforming the mesh. A pole with three edges is called an **N-Pole**
```{figure} ../../assets/modeling/n_pole.png

```
and one with five edges, usually formed as a result of [extrusion](mesh_editing:tools), is called an **E-Pole**.
```{figure} ../../assets/modeling/e_pole.png

```
These two kinds of poles can form naturally and are not always possible to get rid of. On the other hand, poles with six or more edges should be avoided.



## Viewport Shading

To have a better look at the mesh you are working on, you may want to change the type of `Viewport Shading`. The default is the `Solid Mode`, which renders the mesh objects in grayscale and assumes the light comes from the point of view. 

```{figure} ../../assets/modeling/viewport_shading.png

```
If you want to check the overall structure of the mesh, you can switch it to `Wireframe Mode` by pressing <kbd>Z</kbd> and choosing `Wireframe` or <kbd>Left Mouse Click</kbd> on the icon located on the right part of the header. In this mode, faces will not be shaded, allowing you to see vertices and edges more clearly.

```{figure} ../../assets/modeling/wireframe.png
:width: 100%
```

Sometimes you need to see and select the vertices/edges/faces on the other side of the mesh, toggling on **X-Ray** by pressing <kbd>Alt + Z</kbd> or <kbd>Left Mouse Click</kbd> on its icon allows you to do that.

```{figure} ../../assets/modeling/x-ray.png
:width: 100%
```

The other two views, `Material Preview` and `Rendered`, will be introduced in later chapters.

(mesh_editing:tools)=
## Mesh editing tools

::::{tab-set}

:::{tab-item} Select
Basic selecting works the same as in object mode (see the [last section](object:tools) for details), just make sure you are in the right select mode (vertex/edge/face). To make mesh editing easier, edit mode offers a lot more select tools, and you can find them in the `Select` menu on the header. Many of them are quite situational, but **Select Loops** is the one you are going to use all the time. Hold <kbd>Alt</kbd> and <kbd>Left Mouse Click</kbd> on an edge to select the whole edge loop, and it works in all 3 select modes.


```{tip}
:class: margin
**Select Loops** only select the well-defined part of a loop.
```

```{figure} ../../assets/modeling/mesh_select_loop.gif
:width: 100%
```

**Select Random** helps you make irregular shapes. Choose `Select > Select Random` to add random vertices/edges/faces to the selection, depending on the current `Select Mode`.
```{tip}
:class: margin
Check the **Scale** tab for the scaling operation in this example.
```
```{figure} ../../assets/modeling/mesh_select_random.gif
:width: 100%
```

```{tip}
:class: margin
Check **Move**, **Extrude**, and **Inset** tabs for the other tools used in this example.
```
**Checker Deselect** is useful for creating interesting patterns. Select the vertices/edges/faces first, then choose `Select > Checker Deselect` to get the effect.
```{figure} ../../assets/modeling/mesh_select_checker.gif
:width: 100%
```

For more complex meshes, **Select Linked** is useful to get all connected parts. Move the cursor to the part of the mesh you want to select, then press <kbd>L</kbd> to select all connected vertices/edges/faces. Alternatively, select a vertex/edge/face, then choose `Select > Select Linked > Linked`.
```{figure} ../../assets/modeling/mesh_select_linked.gif
:width: 100%
```

:::


:::{tab-item} Move
Similar to moving objects, you can press <kbd>G</kbd> to move vertices/edges/faces in edit mode. Locking on axes and snapping are also available here.

```{figure} ../../assets/modeling/mesh_move.gif
:width: 100%
```

One useful addition is called **Edge Slide**, and it allows you to move vertices along edges and edges along faces. To activate it, select the vertices or edges and press <kbd>G</kbd> twice. If you want to go beyond the limit of the edges/faces, press <kbd>C</kbd> to toggle `Clamping`.

```{figure} ../../assets/modeling/edge_slide.gif
:width: 100%
```

:::

:::{tab-item} Rotate
Rotating edges and faces are the same as rotating an object, see the [last section](object:tools) for details.

```{figure} ../../assets/modeling/mesh_rotate.gif
:width: 100%
```

:::

:::{tab-item} Scale
Scaling edges and faces are the same as rotating an object, see the [last section](object:tools) for details.

```{figure} ../../assets/modeling/mesh_scale.gif
:width: 100%
```

:::

:::{tab-item} Extrude
**Extrude** is an essential tool for making interesting shapes. It works on vertices/edges/faces, and you can activate it by pressing <kbd>E</kbd> or <kbd>Left Mouse Click</kbd> its icon in the toolbar, then move the new vertices/edges/faces to the desired location. By default, extruded face moves along the normal but you can press <kbd>Z</kbd> to remove this restriction, otherwise locking the movement to axes works the same as the move tool. One quirk of the extrude tool is that unlike most other tools (move, rotate, scale, etc.), <kbd>Right Mouse Click</kbd> does not cancel the operation. Instead, the new vertices/edges/faces will be in the exact same place as the old one, and may cause problems down the line. A simple way to check whether there is a duplication is to select the vertices/edges/faces and try to move them a little. For the alternative extrusion modes, hold down <kbd>Left Mouse Button</kbd> on its icon on the toolbar or press <kbd>Alt + E</kbd>.

```{figure} ../../assets/modeling/extrude.gif
:width: 100%
```

:::
:::{tab-item} Inset Faces
The **Inset** tool comes in handy when you want to create a smaller surface in an existing surface for extrusion or other purposes. Select a face then press <kbd>I</kbd> to inset it, move your cursor to adjust and <kbd>Left Mouse Click</kbd> to confirm or <kbd>Right Mouse Click</kbd> to cancel. You can also inset multiple faces simultaneously by selecting all of them, and if they are connected and you want to inset them separately, check `Indivudial` in the `Inset Faces` menu that appears on the bottom left.

```{figure} ../../assets/modeling/inset.gif
:width: 100%
```

:::

:::{tab-item} Loop Cut
**Loop Cut** is a useful tool to add new edges while keeping the flow of the geometry. Put the cursor to where you want to add the edge loop and press <kbd>Ctrl + R</kbd> or `Edge > Loop Cut and Slide`, then move the cursor toward the direction in which the edge loop goes. <kbd>Scroll</kbd> up to add more loops and down to subtract, <kbd>Left Mouse Click</kbd> to confirm and activate **Edge Slide** (check **Move** tag for the details). This tool does not work well with tris and N-Gons because the loop can not be defined.

```{figure} ../../assets/modeling/loop_cut.gif
:width: 100%
```

You can also use it to cut a single edge or face.

```{figure} ../../assets/modeling/loop_cut_2.gif
:width: 100%
```

:::

:::{tab-item} Knife
The **Knife** tool allows you to add arbitrary edges (and vertices that come with them) to a mesh. Press <kbd>K</kbd> or `Mesh > Knife Topology Tool` to activate it and the cursor turns into a knife shape. Start a cut by <kbd>Left Mouse Click</kbd>, then move the cursor and <kbd>Left Mouse Click</kbd> again to draw a line, and you can keep repeating the process. Unlike most tools in Blender, <kbd>Left Mouse Click</kbd> does not cancel the operation, but it lets you make a new starting point. By default, the tool only cuts the visible part of the mesh (even when X-ray mode is on), press <kbd>C</kbd> to cut through the entire mesh to alter that behavior. Press <kbd>Enter</kbd> to confirm the cuts or <kbd>Esc</kbd> to cancel.
```{tip}
:class: margin
- Holding <kbd>Shift</kbd> let you snap to the center of an edge.
- The knife tool is powerful but you can easily create bad topology with it if you are not careful, try other options(like `Loop Cut`) first.
```


```{figure} ../../assets/modeling/knife.gif
:width: 100%
```


:::

:::{tab-item} Bevel
No edge on real-life objects are as sharp as the default cube, and the **Bevel** tool allows you to make rounded edges. Select the edges you want to bevel, then press <kbd>Ctrl + B</kbd> or `Edge > Bevel Edges` to activate the tool. Drag the cursor to adjust the width and <kbd>Scroll</kbd> to increase or decrease the number of segments, then <kbd>Left Mouse Click</kbd> to confirm or <kbd>Right Mouse Click</kbd> to cancel.

```{figure} ../../assets/modeling/bevel.gif
:width: 100%
```

:::

:::{tab-item} Subdivide
The **Subdivide** tool gives you more polygons to work with. Select the faces you want to divide, then <kbd>Right Mouse Click</kbd> and choose `Subdivide`.

```{figure} ../../assets/modeling/subdivide.gif
:width: 100%
```

:::

:::{tab-item} Delete/Dissove
Select the vertices/edges/faces to delete and press <kbd>X</kbd> to bring up the `Delete` menu, then choose to `Delete`/`Dissolve` them. Deleting vertices/edges will also delete the edges/faces which are dependent on them; dissolving will try to keep the geometry intact.

```{figure} ../../assets/modeling/mesh_delete.gif
:width: 100%
```

:::

:::{tab-item} Merge
Select the vertices to merge and press <kbd>M</kbd> to bring up the `Merge` menu, then choose an option to decide where the merged vertex should be.


```{figure} ../../assets/modeling/merge.gif
:width: 100%
```

:::

:::{tab-item} Rip
The **Rip** tool makes copies of selected vertices/edges and creates a hole in the geometry, press <kbd>V</kbd> or choose the `Rip Region` tool in the toolbar to activate it.
```{tip}
:class: margin
The vertices/edges selected after ripping depends on the position of your cursor.
```
```{figure} ../../assets/modeling/rip.gif
:width: 100%
```

:::

:::{tab-item} Fill
The **Fill** tool lets you connect vertices to make new edges or faces. For the former, select two vertices and press <kbd>F</kbd>; for the latter, select 3 or more vertices (2 or more edges work too) then press <kbd>F</kbd>.

```{figure} ../../assets/modeling/fill.gif
:width: 100%
```

If the new face you are trying to create is going to be an N-Gon, **Grid Fill** can help you avoid that. Select the edges (This tool only works on a closed edge loop or a pair of opposite edge loops) and press <kbd>Ctrl + F</kbd> or <kbd>Left Mouse Click</kbd> `Face` on the header to bring up the face menu, then choose `Grid Fill`. 
```{figure} ../../assets/modeling/grid_fill.gif
:width: 100%
```

:::

:::{tab-item} Separate 
Reusing part of an existing object can save you a lot of time. Select a part of a mesh (copy it first if you still need it in the original) and press <kbd>P</kbd> or choose `Mesh > Separate` on the header to bring up the `Separate` menu, then select `Selection`.


```{figure} ../../assets/modeling/separate.gif
:width: 100%
```

:::

:::{tab-item} Proportional Editing
**Proportional Editing** is not a mesh editing tool by itself, but tuning it on allows **Move**/**Rotate**/**Scale** tool to influence adjacent vertices/edges/faces. Press <kbd>O</kbd> or <kbd>Left Mouse Click</kbd>

```{figure} ../../assets/modeling/suzanne_proportional_1.gif
:width: 100%
```

It is especially helpful if you need to edit high poly mesh.

```{figure} ../../assets/modeling/suzanne_proportional_2.gif
:width: 100%
```

:::

::::

Check the end of this chapter to see how these essential tools are used in mesh modeling.

## Tips

::::{tab-set}

:::{tab-item} Low poly
```{tip}
:class: margin
Use **Proportional Editing** may help if you need to edit High poly mesh.
```
Always start with low poly mesh. High poly mesh is harder to work with, and it is much easier to turn low poly mesh into high poly ones (e.g. adding a [Subdivide Surface modifier](modifier:common)) than the opposite.

```{figure} ../../assets/modeling/suzanne_low_high_poly.gif
:width: 100%
```


:::

:::{tab-item} Topology
**Topology** refers to the distribution of vertices, edges, and faces in 3D modeling, and how to keep it clean is an important but complicated topic. For beginners, following these points would be a good start:

- Avoid N-Gon, and try to use quad as much as possible
- Keep mesh density even
- Keep an eye on duplicated vertices, edges, and faces, especially when extruding
- Make sure normals are pointing right directions

:::

:::{tab-item} Use Reference
It definitely helps to make your 3D model look right if you have reference pictures. To add a reference image to the viewport, drag the file into the viewport or press <kbd>Shift + A</kbd> and choose `Image > Reference` and find the file in the browser. Adjust the location and rotation of the references for the three views so they line up, then <kbd>Left Mouse Click</kbd> on the cursor icon in the outliner for the reference objects to disable selection so you will not accidentally select them during modeling. Finally, you can make them only visible in the front, side, and top views, by unchecking `Object Data Properties > Empty > Show In Perspective`

```{tip}
:class: margin
- If the cursor icon for disabling selection is not there, <kbd>Left Mouse Click</kbd> on the funnel icon on the header of the outliner area, and turn it on under `Restriction Toggles`.
- To prevent the reference images from blocking your 3D object, choose the `Back` option for `Depth` in the `Data` tab of the properties area.
```

```{figure} ../../assets/modeling/reference_img.gif
:width: 100%
```

:::

::::
