# SharpRay Web

A self-contained browser adaptation of Riley T. Perry's original 2004 C# ray tracer, [SharpRay](https://github.com/Agmash29a/SharpRay).

## Run

Download `index.html` and open it in a current desktop browser. No installation, build step, server, external libraries or internet connection is needed.

Choose a scene and render settings, then select **Render scene**. **Stop** cancels the current render. **Save PNG** exports a completed image. Expand **Edit scene** in Render Studio to change the background, camera, lights, geometry and materials. **Render scene** validates and applies these edits. Colour values use colour pickers; lights share a consistent control layout.

## Features

- 16 presets: seven adapted original scenes, three browser demonstrations and six new compositions.
- Mountain Generator in the scene selector: MountainGen-HTML seeded subdivision, detail 2–7, roughness, palettes, snowline and reflective water.
- OBJ import with polygon triangulation, automatic centring/scaling and triangle BVH acceleration; up to 20 MB / 50,000 triangles. Flat shading; MTL materials and textures are not loaded.
- Recursive reflections, Snell refraction with Fresnel blending, Phong shading and shadows.
- Spheres, ellipsoids, planes, boxes, triangles, discs and open cylinders.
- Checkerboard, marble and wood procedural textures.
- Drag to spin and tilt, wheel to zoom, and double-click or Reset view to restore the camera. Camera controls remain locked until a render completes.
- Supersampling and adjustable recursion depth.
- Background-worker rendering with progress reporting.
- Full-width padded black render view with a compact white interface. Scene information, scene-specific controls and Render Studio sit below the image.
- Collapsed-by-default scene editor with object selection for large meshes; no JSON import/export UI.

## Reading the source

All HTML, CSS and JavaScript lives in `index.html`:

1. Interface markup and styling.
2. The `engine` script: vector operations, `hitObject`, `hitObjects`, `getColour`, `traceRay`, `calculateUVW`, and the worker rendering loop.
3. `mountain-generator`: seeded terrain generation and material zoning.
4. `obj-parser`: OBJ parsing and polygon triangulation.
5. Browser interface, scene builders and editable draft controls.

Relevant comments from the C# source are included with source-file references. Browser-specific changes are labelled. Arrays represent vectors and colours. Internal scene property names preserve the original adaptation: `color` corresponds to `cd`, `shininess` to `n`, `eye` to `e`, and `target` to `l`.

## Original source and differences

Adapted from original commit `8b16f787edd2bf5595f8b37c2ab01fd54b59002a` in Agmash29a/SharpRay. This is a core adaptation, not a complete or pixel-identical port of the C# application. Camera framing and shading differ; the browser uses new procedural noise approximations and Fresnel blending.

Not included: legacy PLY loading, torus quartic intersections, transformed instances, image textures, or the complete original scene catalogue. Glass casts opaque shadows; caustics and global illumination are not simulated.

## Validation

All 16 presets were smoke-rendered. The readability refactor was checked against the previous browser version at two camera angles per preset: all 32 low-resolution comparisons produced identical pixel bytes. These comparisons establish refactor equivalence, not parity with the original C# renderer.

Latest changes were checked with script syntax and focused tests for camera locking, colour conversion, terrain generation, OBJ parsing and scene editing. Recent UI changes have not been visually verified because browser execution was blocked by the development environment.

## Attribution

Original SharpRay: © 2004 Riley T. Perry — Chillers of Entropy.

Browser adaptation developed for Riley T. Perry. No new open-source licence is granted by this repository; the owner can choose a licence separately.
