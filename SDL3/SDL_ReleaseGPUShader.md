###### (This is the documentation for SDL3, which is under heavy development and the API is changing! [SDL2](https://wiki.libsdl.org/SDL2/) is the current stable version!)
# SDL_ReleaseGPUShader

Frees the given shader as soon as it is safe to do so.

## Header File

Defined in [<SDL3/SDL_gpu.h>](https://github.com/libsdl-org/SDL/blob/main/include/SDL3/SDL_gpu.h)

## Syntax

```c
void SDL_ReleaseGPUShader(
    SDL_GPUDevice *device,
    SDL_GPUShader *shader);
```

## Function Parameters

|                                  |            |                           |
| -------------------------------- | ---------- | ------------------------- |
| [SDL_GPUDevice](SDL_GPUDevice) * | **device** | a GPU context.            |
| [SDL_GPUShader](SDL_GPUShader) * | **shader** | a shader to be destroyed. |

## Remarks

You must not reference the shader after calling this function.

## Version

This function is available since SDL 3.0.0.

----
[CategoryAPI](CategoryAPI), [CategoryAPIFunction](CategoryAPIFunction), [CategoryGPU](CategoryGPU)
