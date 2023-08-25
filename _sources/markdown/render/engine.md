(render_engine)=
# Rendering engines
**Rendering Engines** are programs that draw pictures on your screen based on the 3D scene, and you have been using them from the moment you first opened Blender.


## Workbench
**Workbench** is the render engine optimized for modeling, and not intended for the final render. It ignores objects' materials and you can only adjust shading in the `Viewport Shading` dropdown menu. The `Soild` and `Wireframe` shading are both rendered using this engine, and the `X-ray` mode is unique to it.
```{figure} ../../assets/render/monkey_workbench.png
:width: 100%
```


(render_engine:EEVEE)=
## EEVEE
```{tip}
:class: margin
Check the limitations of EEVEE [here](https://docs.blender.org/manual/en/latest/render/eevee/limitations.html).
```
**EEVEE(Extra Easy Virtual Environment Engine)** is the default rendering engine in Blender. Like the vast majority of 3D video games, it uses a technique called **Rasterization** to render the images. It is capable of producing high-quality results but requires more tweaking, and some features do not work with it, like **Displacement** in [shader nodes](PBR_mat).

```{note} 
:class: margin
Apparently those Dutch devs aren't afraid of Nintendo ninjas.
```
```{figure} ../../assets/render/monkey_eevee.png
:width: 100%
```


## Cycles
**Cycles** is a path tracer, which means it simulate how light works in real life and can produce physically-accurate rendering results. It is much heavier than **EEVEE**, and you will need a good GPU to use it in the viewport. In `Edit > Preferences...`, you can set the rendering device in the `System` tab, `CUDA` or `OptiX` for Nvidia GPUs, `HIP` for AMD, and `oneAPI` for Intel.

```{figure} ../../assets/render/monkey_cycles.png
:width: 100%
```