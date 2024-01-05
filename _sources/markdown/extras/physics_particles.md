(phys_parti)= 
# Physics Simulation and Particle System
Blender offers tools to simulate real-world physics with the 3D objects you created, let's see how to set it up.
```{tip} 
:class: margin
Both physics simulation and particle system are modifiers.
```

## Particle System
The `Particles` tab in the properties area is quite similar to the `Material` one. You can add a new **Particle System Slot** to the object by <kbd>Left Mouse Click</kbd> the `+` button, and it will also create a linked **Particle Settings**. There are two kinds of particles, `Emitter` and `Hair`.
::::{tab-set}
:::{tab-item} Emitter
This is how a default emitter looks. In this example, from frame 1 to 120, 1000 particles are randomly generated, and they each exist for 30 frames. You can change these under `Emission`.
```{tip} 
:class: margin
The particles fall because default particles has `Newtonian` as its `Physics Type` and `Gravity` is enabled,  for the latter you can change it in the `Scene` tab.
```
```{figure} ../../assets/extra/parti_emit_1.gif
:width: 100%
```
To change how the particles are rendered, Scroll down to `Render`. Here the ico sphere is raining down stars and donuts by rendering particles as these two objects in a collection.
```{figure} ../../assets/extra/parti_emit_2.gif
:width: 100%
```
Particles can interact with other objects that have physics effects enabled, like the plane in this example, which has a **Collision** physics modifier.
```{figure} ../../assets/extra/parti_emit_3.gif
:width: 100%
```

:::

:::{tab-item} Hair
The default hair is not affected by gravity.
```{figure} ../../assets/extra/parti_hair_1.png
:width: 100%
```
Ticking `Hair Dynamics` enables physics simulation for the hair.
```{figure} ../../assets/extra/parti_hair_2.gif
:width: 100%
```
Enabling `Children` allows you to render more hair without extra simulations.
```{figure} ../../assets/extra/parti_hair_3.gif
:width: 100%
```
:::

:::{tab-item} Use Force Fields
**Force Fields** are generated from objects to influence simulations. All kinds of objects can be used, but the easiest way to try out is feature is to add one in `Add > Force Field` menu. Let's see how **Wind** affects hair.
```{figure} ../../assets/extra/parti_ff_1.gif
:width: 100%
```
They work on emitters too.
```{figure} ../../assets/extra/parti_ff_2.gif
:width: 100%
```
This example is made with a **Turbulence** at the center of the emitter.
```{figure} ../../assets/extra/parti_ff_3.gif
:width: 100%
```
:::

::::


## Physics Simulations
::::{tab-set}
:::{tab-item} Rigid Body
The **Rigid Body** simulates the motion of solid objects, and you can choose between two types: `Passive` and `Active`. A `Passive` body remains static during the simulation, to make a mesh object into one, go to the `Physics` tab in the properties area, <kbd>Left Mouse Click</kbd> the `Rigid Body` button, then set the `Type` to `Passive`. 
```{tip} 
:class: margin
If your object have a big concave surface like this one, change `Collision Shape` from `Convex Hull` to `Mesh`.
```
```{figure} ../../assets/extra/phys_rigid_plane.png
:width: 100%
```
````{tip} 
:class: margin
The pawn is imported from a previous project through `File > Append...`.
```{figure} ../../assets/extra/append.gif
:width: 100%
```
```````
An `Active` body will be dynamically simulated, add `Rigid Body` to the mesh object and make sure the `Type` is `Active`.
```{figure} ../../assets/extra/phys_rigid_pawn.png
:width: 100%
```
Hit <kbd>Spacebar</kbd> to run the simulation.
```{figure} ../../assets/extra/phys_rigid_demo.gif
:width: 100%
```
:::

:::{tab-item} Liquid
To make basic a flow of fluid, first you need a `Domain`, which defines the space where the liquid simulation happens. To make a mesh object a `Domain` for liquid simulation, go to the `Physics` tab in the properties area, <kbd>Left Mouse Click</kbd> the `Fluid` button, then set the `Type` to `Domain` and `Settings > Domain Type` to `Liquid`.
```{tip} 
:class: margin
- This also adds a `Liquid` particle system and two modifiers to the object.
- The properties of the simulated fluid are also set in this panel.
```
```{figure} ../../assets/extra/phys_liquid_domain.png
:width: 100%
```
You will also need a vessel to collect the fluid. Make one and move it inside the `Domain`, give it fluid physics but set `Type` to `Effector` this time. If the mesh is unclosed, tick `Is Planar`.
```{figure} ../../assets/extra/phys_liquid_effector.png
:width: 100%
```
To complete this setup, Blender needs to know where to create the fluid. Add a small object and move it inside the `Domain`, and make it a `Flow` type in fluid physics and set `Settings > Flow Type` to `Liquid` and `Flow Behavior` to `Inflow`.
```{tip} 
:class: margin
Use the size of the object and `Settings > Initial Velocity` to control the amount of fluid generated.
```
```{figure} ../../assets/extra/phys_liquid_inflow.png
:width: 100%
```
Hit <kbd>Spacebar</kbd> and you should see the simulation happening.
```{figure} ../../assets/extra/phys_liquid_particle.gif
:width: 100%
```
To Render the fluid, you need to turn it into a mesh. Select the **Domain** object, tick `Liquid > Mesh`, then restart the animation from frame 1. 

```{figure} ../../assets/extra/phys_liquid_mesh.gif
:width: 100%
```
Add the liquid material to the **Domain** object, hide the **Flow** object, and don't forget to set **Shade Smooth**.
```{tip} 
:class: margin
You can increase `Settings > Resolution Divisions` for a more detailed result if your computer can handle it.
```
```{figure} ../../assets/extra/phys_liquid_render.gif
:width: 100%
```
````{admonition} Water in Glass
:class: dropdown
Sometimes water may look seperated to the glass holding it. This is because water and glass are separate mesh, when the refraction is calculated, the rendering engine acts like there is a layer of air inbetween.
```{figure} ../../assets/extra/phys_water_trick_1.png.
:width: 100%
```
A simple way to fix it is to scale up the water mesh, making the two meshes to overlap slightly.
```{figure} ../../assets/extra/phys_water_trick_2.png.
:width: 100%
```
````
:::

:::{tab-item} Cloth
To run a cloth simulation, first you need to have enough polygons on the mesh. If it doesn't, use `Subdivide` in edit mode or add a **Subdivide Surface** modifier. Then go to the `Physics` tab in the properties area, <kbd>Left Mouse Click</kbd> the `Cloth` button. The other objects in the scene need to have a **Collision** physics modifier to interact with the **Cloth** object. 
```{tip} 
:class: margin
Cloth simulation is quite computationally intensive and Blender may freeze if you try to run it in real-time. A safer way is to calculate the physics simulation before the animation starts, also known as **Baking**. To bake the simulation, <kbd>Left Mouse Click</kbd> `Cache > Bake`.
```
```{figure} ../../assets/extra/phys_cloth_1.gif
:width: 100%
```
Add a **Subdivide Surface** modifier after the **Cloth** modifier and set **Shade Smooth** to make it less blocky.
```{figure} ../../assets/extra/phys_cloth_2.gif
:width: 100%
```
It also interacts with force fields like **Wind**.
```{figure} ../../assets/extra/phys_cloth_3.gif
:width: 100%
```
:::
::::


