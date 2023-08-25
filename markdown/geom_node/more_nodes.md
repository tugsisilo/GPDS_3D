(gn_more_nodes)=

# More about Geometry Node
The `Add` menu in the geometry node editor looks much more crowded than the shader node one, but you do not have to know all the nodes to start using it. In this section, we will go through some of the most used nodes.

## Keyframe and Driver
The values in the input sockets of the nodes can be keyframed like any other properties, and adding drivers is also possible.
```{figure} ../../assets/geom_node/gn_kf_driver.gif
:width: 100%
```

## More Nodes
For `Texture`, `Group`, `Layout`, and most of the `Utilities` nodes, check [shader nodes](shader_node_tree).
::::{tab-set}

:::{tab-item} Attribute


````{card} Capture Attribute
The **Capture Attribute** node can save field outputs for later use. In this example, the node saves the postion of the corners of the cube, and by subtracting the current position of the instances, we can get the vector to rotate the cones to always point at the corners.
```{tip}
The difference between two locations gives a vector pointing from one to the other.
```
```{figure} ../../assets/geom_node/cap_attr.gif
:width: 100%
```

````

````{card} Store Named Attribute
The **Store Named Attribute** node is very similar to the **Capture Attribute** node, the difference is you need a **Named Attribute** node when you read the stored attribute.
```{figure} ../../assets/geom_node/store_attr.gif
:width: 100%
```

````

:::

:::{tab-item} Input


````{card} Constant
Nodes here are similar to the **Value** node in shader nodes but comes in different types. Use them as an input to control different input at the same time.
````

````{card} Group
You can find the **Group Input** node here if the default one is deleted.
````


````{card} Scene > Collection Info
If you want to put instances of a series of different object on points, you can put them in a collection and bring the whole collection in using **Collection Info**. Ticking `Separate Children` in this node and `Pick Instance` in the `Instance on Points` node will give you the effect in the example.
```{figure} ../../assets/geom_node/col_info.png
:width: 100%
```
````

````{card} Scene >  Object Info
The **Object Info** node allows you to bring an object into the node tree.
```{figure} ../../assets/geom_node/obj_info.png
:width: 100%
```
````

````{card} Scene >  Is Viewport
When you are working with a lot of meshes in a scene, like foliage, the 3D viewport can get irresposive due to high polygon count. The **Is Viewport** node along with a **Switch** node allows you to replace the actual object with low-poly proxies in the viewport.

In viewport:
```{figure} ../../assets/geom_node/viewport_proxy.png
:width: 100%
```

Render:
```{figure} ../../assets/geom_node/viewport_proxy_render.png
:width: 100%
```
````

:::

:::{tab-item} Output
````{card} Group Output
If you accidentally deleted **Group Output** you can find it here.
````

````{card} Viewer
The **Viewer** node allows you to check data and geometry inside a node tree. <kbd>Ctrl + Shift + Left Mouse Click</kbd> on a node to connect it to a **Viewer** node.
```{figure} ../../assets/geom_node/viewer.png
:width: 100%
```

````

:::

:::{tab-item} Geometry
`````{card} Read
Nodes here provide fields for retrieving geometry infomation, you can find them in examples for other nodes and the projects at the end of the chapter.
`````


````{card} Sample > Geometry Proximity
The **Geometry Proximity** node calculates the closest distance to the target geometry or the closest location on the target to the surface. In this example, the density of the points on the surface is controlled by the distance to the cube object.

```{figure} ../../assets/geom_node/geom_proximity.gif
:width: 100%
```
````

````{card} Sample > Raycast
The **Raycast** node projects the source object onto the target. `Ray Direction` controls the direction of the projection and `Ray Length` restricts the maximum distance of this effect, and the node can output how the target is "hit". This example shows how you can move cubes in a grid with this node.

```{figure} ../../assets/geom_node/raycast.gif
:width: 100%
```
````


````{card} Write > Set Position
The **Set Position** node can change the position of points/vertices/control points. You can filter the points you want to move using the `Selection` input, set their new position in `Position`, or move them based on vectors with "Offset". See how this node works in examples for nodes like **Capture Attribute**, **Raycast**, etc. 

````

````{card} Operations > Transform Geometry
The **Transform Geometry** node changes the position of the location, rotation, and scale of the input geometry, similar to the `Item > Transform` menu in the sidebar of the viewport. See its usage in the projects section at the end of this chapter.

````

````{card} Operations > Bounding Box
A **Bounding Box** is the minimum box mesh that encapsulates a geometry, and the **Bounding Box** node creates one for the input geomery. The `Bounding Box` socket gives the box mesh, and the `Min` and `Max` sockets outputs the -X/-Y/-Z and +X/+Y/+Z location of the box respectively.

```{figure} ../../assets/geom_node/b_box.png
:width: 100%
```

````

````{card} Join Geometry
The **Join Geometry** node can take any number of geometry inputs and merge them into one. With Node Wrangler enabled, hold <kbd>Ctrl + Shift + Right Mouse Button</kbd> on a node with geometry output then drag it onto anther one will create this node with these two nodes linked to it.

````


:::

:::{tab-item} Curve
Nodes in this submenu can help you make new curves, modify curves, or read curve-related data. In this example, the `Primitive` nodes (like **Bezier Segment**, **Curve Circle**) make their respective curves, the `Read` nodes (like **Endpoint Selection**, **Spline Parameter**) retrieve information from the Bezier curve, the `Write` nodes(**Subdivide Curve**, **Set Curve Radius**, **Set Curve Tilt**, ) modify the curve, and **Curve to Mesh**, one of the `Operation` nodes, turn the curve into a mesh with a profile.

```{figure} ../../assets/geom_node/curve_nodes.png
:width: 100%
```
:::

:::{tab-item} Instances
Apart from the **Instance on Points** node we have been using, nodes here can move/rotate/scale instances. 

```{figure} ../../assets/geom_node/inst_nodes.png
:width: 100%
```


:::

:::{tab-item} Mesh
Although not as versatile as the manual mesh editing tools, the nodes in the `Mesh` submenu are powerful in their own ways. In this example, the same node tree is applied to 3 different meshes creating different results. The **Dual Mesh** node converts faces to vertices and vertices to faces, other nodes are self-explanatory.
```{tip}
:class: margin
Remember the geometry node group acts like a node group, you can add input and output sockets to it.
```
```{figure} ../../assets/geom_node/mesh_nodes.png
:width: 100%
```

Another notable one is the **Mesh to Volume** node, combined with the **Distribute Points in Volume** node, you can generate points inside a geometry. In this example, the cones are placed randomly inside the source object (a cube) and pointing at the empty object.
```{figure} ../../assets/geom_node/mesh2vol.gif
:width: 100%
```

:::

:::{tab-item} Material

````{card} Set Material
You can assign different material to different parts of the geometry using **Set Material** node.
```{tip}
You can choose any material in the data.
```
```{figure} ../../assets/geom_node/set_mat.png
:width: 100%
```

````

:::

:::{tab-item} Utilities

````{card} Rotation > Align Euler to Vector
The **Align Euler to Vector** node allows you to align geometry with the direction of a vector. See the examples for the **Capture Attribute** and **Mesh to Volumn** node.


````

````{card} Random Value
The **Random Value** node can help you create some variaty by generating random value of different types. Check examples for other nodes to see this node in action.
````

:::

:::{tab-item} Simulation Zone
The **Simulation Zone** allows you to create custom physics effects by enabling one frame to influence the next. In this example, the **Set Position** node moves the points in a random direction every frame, and the random seed is changed per frame too.
```{figure} ../../assets/extra/sim_node.gif
:width: 100%
```

:::
::::
