# OpenGL Graphics Engine

A small 3D engine written from scratch in C++ and OpenGL 3.3 for a university computer
graphics course (COMP3340, University of Newcastle, 2024). It renders a scene of
PBR-textured models lit by a moving sun, with real-time shadows and a procedural cloud sky.

I was the lead developer on a team of three and wrote most of the engine: the
entity-component system, the renderer, PBR and shadow-mapping shaders, model loading, the
camera and input, and the day/night cycle. Teammates contributed the lighting manager, the
cloud shader and the wind turbine model import. The project received full marks.

The version submitted for assessment is archived, unchanged, at
[COMP3340GraphicsEngine2](https://github.com/JacobSchepis/COMP3340GraphicsEngine2). This
repo continues from it, with the full commit history.

<!-- TODO: add a screenshot or GIF of the running scene here -->

## Features

- **Entity-component system** with a Unity-style `Monobehavior` lifecycle (`awake`,
  `start`, `update`), so behaviour like the camera controller and the sun cycle are
  components attached to entities.
- **Physically based rendering** with albedo, normal, roughness, metallic and ambient
  occlusion maps.
- **Shadow mapping** for directional lights: a depth pass per light, then a lit pass that
  samples each light's shadow map.
- **Day/night cycle** that rotates the sun and shifts its colour over time.
- **Procedural clouds** drawn with a noise-based fragment shader.
- **Model loading** of OBJ files and their materials through Assimp.
- **Free-fly camera** with mouse look.

## Built with

C++, OpenGL 3.3 (core profile), GLSL, SDL2, GLEW, GLM, Assimp, stb_image, CMake.

## Project layout

| Folder | What's in it |
| --- | --- |
| `src/`, `include/` | Engine code, split into components, entities, graphics, systems, scripts, input and util |
| `shaders/` | GLSL shaders: PBR, shadow map, clouds, outline, full-screen quad |
| `resources/` | Models and textures |
| `lib/`, `dll/`, `include/` (third-party) | Prebuilt SDL2, GLEW and Assimp for Windows |

## Building and running

Windows only, since the third-party libraries are prebuilt for MSVC (x64).

1. Open the folder in Visual Studio 2022 (with the "Desktop development with C++" workload).
2. Pick the `x64-debug` CMake preset and build.
3. Run `COMP3340GraphicsEngine2.exe`. CMake copies the shaders, models and DLLs next to it.

## Controls

| Key | Action |
| --- | --- |
| W A S D | Move |
| Mouse | Look around |
| Space / Left Ctrl | Move up / down |
| Esc | Release the mouse cursor |
