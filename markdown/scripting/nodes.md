(node_scripting)=
# Node Scripting
You have already seen the power of the node trees in Blender, and now you can make them with Python script.

## Shader Nodes
Continuing from the last section, after creating a new material with `use_nodes` turned on
```python
mat = bpy.data.materials.new("new_mat")
mat.use_nodes = True
```
You will need the **Material Output** but not necessarily the **Principled BSDF** node. To delete a node, use
```python
mat.node_tree.nodes.remove(mat.node_tree.nodes['Principled BSDF'])
```

To add nodes to the node tree, specify their type and assign them to a variable for later use
```{tip}
:class: margin
Check shader node type(subclasses) [here](https://docs.blender.org/api/current/bpy.types.ShaderNode.html).
```
```python
fresnel_0 = mat.node_tree.nodes.new("ShaderNodeFresnel")
math_node_0 = mat.node_tree.nodes.new("ShaderNodeMath")
#move the nodes bit for demostration
fresnel_0.location = (-200, 300)
math_node_0.location = (0, 300)
```
You can tweak the nodes and change the inputs for unconnected sockets
```{tip}
:class: margin
- Check math operation types [here](https://docs.blender.org/api/current/bpy_types_enum_items/node_math_items.html).
- You may think it is much easier to do math in Python compared to using `Math` nodes, but Blender will not be able to compile the shader without them.
- You can specify the socket by its name or index, but using index will be easier if a node have multiple sockets with the same name.
```
```python
math_node_0.operation = "MULTIPLY"
math_node_0.inputs[1].default_value = 0.7
```
then connect the nodes
```python
mat.node_tree.links.new(fresnel_0.outputs[0], math_node_0.inputs[0])
mat.node_tree.links.new(math_node_0.outputs[0], mat.node_tree.nodes['Material Output'].inputs[0])
```

```{figure} ../../assets/scripting/s_node_demo.gif

```

```{note}
The nodes will stack on each other in the shader editor if you don not specify their location. An easy solution is to use the **Node Arrange** add-on, enable it and select a node in the editor, then <kbd>Left Mouse Click</kbd> `Arrange > Node Arrange > Arrange All Nodes`.
```
## Geometry Nodes
You can create a new geometry node group in the data by
```python
new_geom_group = bpy.data.node_groups.new("GROUP_NAME", "GeometryNodeTree")
```
Unlike a new geometry node group created in the GUI, this new group is empty, with no **Group Input** or **Group Output** nodes. You can add them back
```python
geom_input = new_geom_group.nodes.new("NodeGroupInput")
geom_output = new_geom_group.nodes.new("NodeGroupOutput")
```
```{tip}
:class: margin
- Check socket type(subclasses) [here](https://docs.blender.org/api/current/bpy.types.NodeSocketStandard.html).
- Check geometry node type(subclasses) [here](https://docs.blender.org/api/current/bpy.types.GeometryNode.html). Some nodes, like **Value** and **Math**, are the same as shader nodes you can find them there.
```
but these nodes will have no input/output sockets. To create new sockets, you need to add them directly to the node group
```python
new_geom_group.inputs.new("NodeSocketGeometry", "Geometry")
new_geom_group.outputs.new("NodeSocketGeometry", "Geometry")
```
and now you have the familiar starting node tree. Adding and connecting nodes are the same as in shader nodes.

As explained in the previous chapter, applying geometry nodes to an object requires adding a **Geometry Nodes** modifier.
```python
obj.modifiers.new("MODIFIER_NAME", "NODES")
obj.modifiers["MODIFIER_NAME"].node_group = new_geom_group
```

## Compositor Nodes
Enabling compositor nodes for the current scene is simple
```python
bpy.context.scene.use_nodes = True
```
and you may want to make a convenience variable for the node tree
```python
compo_nodes = bpy.context..scene.node_tree
```
```{tip}
:class: margin
Check compositor node type(subclasses) [here](https://docs.blender.org/api/current/bpy.types.CompositorNode.html).
```
Adding and connecting nodes are the same as above.


