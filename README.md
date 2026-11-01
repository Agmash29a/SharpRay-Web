# SharpRay Web

A self-contained browser adaptation of Riley T. Perry's original 2004 C# ray tracer, [SharpRay](https://github.com/Agmash29a/SharpRay).

## Run

Download `index.html` and open it in a current desktop browser. No installation, build step, server, external libraries or internet connection is needed.

Choose a scene and render settings, then select **Render scene**. **Stop** cancels the current render. **Save PNG** exports a completed image. The JSON editor supports editing, importing and exporting scenes.

## Features

- 16 scenes: seven adapted original scenes, three browser demonstrations and six new compositions.
- Recursive reflections, Snell refraction with Fresnel blending, Phong shading and shadows.
- Spheres, ellipsoids, planes, boxes, triangles, discs and open cylinders.
- Checkerboard, marble and wood procedural textures.
- Camera orbit/distance controls, supersampling and adjustable recursion depth.
- Background-worker rendering with progress reporting.
- White interface with a black render-window backdrop.

## Reading the source

All HTML, CSS and JavaScript lives in `index.html`:

1. Interface markup and styling.
2. The `engine` script: vector operations, `hitObject`, `hitObjects`, `getColour`, `traceRay`, `calculateUVW`, and the worker rendering loop.
3. Browser interface and scene builders.

Relevant comments from the C# source are included with source-file references. Browser-specific changes are labelled. Arrays represent vectors and colours. Existing JSON property names remain compatible: `color` corresponds to `cd`, `shininess` to `n`, `eye` to `e`, and `target` to `l`.

## Original source and differences

Adapted from original commit `8b16f787edd2bf5595f8b37c2ab01fd54b59002a` in Agmash29a/SharpRay. This is a core adaptation, not a complete or pixel-identical port of the C# application. Camera framing and shading differ; the browser uses new procedural noise approximations and Fresnel blending.

Not included: legacy mesh/PLY loading, torus quartic intersections, transformed instances, image textures, or the complete original scene catalogue. Glass casts opaque shadows; caustics and global illumination are not simulated.

## Validation

All 16 presets were smoke-rendered. The readability refactor was checked against the previous browser version at two camera angles per preset: all 32 low-resolution comparisons produced identical pixel bytes. These comparisons establish refactor equivalence, not parity with the original C# renderer.

## Attribution

Original SharpRay: © 2004 Riley T. Perry — Chillers of Entropy.

Browser adaptation developed for Riley T. Perry. No new open-source licence is granted by this repository; the owner can choose a licence separately.
