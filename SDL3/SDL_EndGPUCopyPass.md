###### (This is the documentation for SDL3, which is the current stable version. [SDL2](https://wiki.libsdl.org/SDL2/) was the previous version!)
# SDL_EndGPUCopyPass

Ends the current copy pass.

## Header File

Defined in [<SDL3/SDL_gpu.h>](https://github.com/libsdl-org/SDL/blob/main/include/SDL3/SDL_gpu.h)

## Syntax

```c
void SDL_EndGPUCopyPass(
    SDL_GPUCopyPass *copy_pass);
```

## Function Parameters

|                                      |               |                     |
| ------------------------------------ | ------------- | ------------------- |
| [SDL_GPUCopyPass](SDL_GPUCopyPass) * | **copy_pass** | a copy pass handle. |

## Version

This function is available since SDL 3.1.3.

----
[CategoryAPI](CategoryAPI), [CategoryAPIFunction](CategoryAPIFunction), [CategoryGPU](CategoryGPU)

