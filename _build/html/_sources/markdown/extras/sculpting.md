(Sculpting)=
# Sculpting
**Sculpting** is the feature for making detailed organic-looking meshes. It is analogous to clay sculpting and requires more artistic skills compared to modeling.

```{note}
A pen tablet or display tablet is recommended, but you can try it out with your mouse.
```

## Preparation
First, you need to be sure the object you want to sculpt is a mesh object. If not, you need to convert it to a mesh first. To do that, select the object and <kbd>Right Mouse Click</kbd> then choose `Convert to > Mesh`.
```{figure} ../../assets/extra/to_mesh.gif
:width: 100%
```
A mesh object has a **Sculpt Mode** in the viewport, and all sculpting will be done there. But before that, a mesh needs enough polygons to be sculpted.
```{figure} ../../assets/extra/mesh_0.gif
:width: 100%
```
There are multiple ways to make a mesh more high-poly, and some of them you already know. You can `Subdivide` the mesh in edit mode
```{figure} ../../assets/extra/mesh_subdiv.gif
:width: 100%
```
or give the object a `Subdivide Surface` modifier and apply it.
```{figure} ../../assets/extra/mesh_subsurf.gif
:width: 100%
```
Another way is to use the `Remesh` modifier.
```{figure} ../../assets/extra/mesh_remesh.gif
:width: 100%
```
```{tip} 
:class: margin
You can also remesh in sculpt mode, choose `Remesh` on the header, change `Voxel Size` (smaller value gives finer result) and <kbd>Left Mouse Click</kbd> the `Remesh` button.
```

You can also use the `Dynatopo(Dynamic Topology)` feature in the sculpt mode. By default, it automatically subdivides the surface when you sculpt based on how zoomed in you are.
```{figure} ../../assets/extra/mesh_dynatopo.gif
:width: 100%
```
For symmetrical objects, you can toggle on mesh symmetry on the desired axes.
```{figure} ../../assets/extra/sculpt_mirror.gif
:width: 100%
```
To see the mesh better during sculpting, you may want to use `MatCap(Material capture)` instead of the default `Studio` Shading. To do that, open the `Viewport Shading` menu and switch `Lighting` to `MatCap` then choose the one you like.
```{figure} ../../assets/extra/matcap.gif
:width: 100%
```

## Basic Sculpting Tools
```{tip} 
:class: margin
when using a tablet, the toggles on the right of the `Radius` and `Strength` controls whether the pressure influence the respective property of the brush.
```
In sculpt mode, the new icons in the toolbar are **Brushes**. The brushes are the main tool for us to interact with meshes, and they have some common properties. Press <kbd>F</kbd> to adjust the `Radius` of a brush and <kbd>Shift + F</kbd> for the `Strength`, or use the sliders on the header. 
```{figure} ../../assets/extra/brush_basics_0.gif
:width: 100%
```
For the brushes that have a direction, you can use the `+/-` button on the header to switch between them, or hold <kbd>Control</kbd> to temporarily inverse the effect.
```{figure} ../../assets/extra/brush_basics_1.gif
:width: 100%
```
::::{tab-set}
:::{tab-item} Draw
**Draw** is the most basic sculpting brush, it moves vertices inwards/outwards.
```{figure} ../../assets/extra/brush_draw.gif
:width: 100%
```
:::

:::{tab-item} Draw Sharp
**Draw Sharp** is very similar to **Draw**, but with a sharp falloff.
```{figure} ../../assets/extra/brush_drawsharp.gif
:width: 100%
```
:::

:::{tab-item} Clay Strip
**Clay Strip** is useful for building/removing volume, and usually you need to use **Smooth** afterward.
```{figure} ../../assets/extra/brush_clay.gif
:width: 100%
```
:::

:::{tab-item} Smooth
The **Smooth** brush smooths the surface. Because this brush is used so often, you can hold <kbd>Shift</kbd> while using other brushes to temporarily access it.
```{figure} ../../assets/extra/brush_smooth.gif
:width: 100%
```
:::

:::{tab-item} Grab
**Grab** is useful for creating the general shape of an object.
```{figure} ../../assets/extra/brush_grab.gif
:width: 100%
```
:::

:::{tab-item} Inflate
**Inflate** is similar to **Draw**, but it makes vertices move along their normals.
```{figure} ../../assets/extra/brush_inflate.gif
:width: 100%
```
:::

:::{tab-item} Snake Hook
**Snake Hook** pulls vertices along with the movement of the brush.
```{figure} ../../assets/extra/brush_snakehook.gif
:width: 100%
```
:::


:::{tab-item} Mask
**Mask** creates a mask that prevents the area from being modified by other sculpting tools.
```{figure} ../../assets/extra/brush_mask.gif
:width: 100%
```
:::


::::