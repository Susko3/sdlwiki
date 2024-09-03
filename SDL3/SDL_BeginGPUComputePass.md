###### (This is the documentation for SDL3, which is under heavy development and the API is changing! [SDL2](https://wiki.libsdl.org/SDL2/) is the current stable version!)
# SDL_BeginGPUComputePass

Begins a compute pass on a command buffer.

## Header File

Defined in [<SDL3/SDL_gpu.h>](https://github.com/libsdl-org/SDL/blob/main/include/SDL3/SDL_gpu.h)

## Syntax

```c
SDL_GPUComputePass* SDL_BeginGPUComputePass(
    SDL_GPUCommandBuffer *commandBuffer,
    SDL_GPUStorageTextureWriteOnlyBinding *storageTextureBindings,
    Uint32 storageTextureBindingCount,
    SDL_GPUStorageBufferWriteOnlyBinding *storageBufferBindings,
    Uint32 storageBufferBindingCount);
```

## Function Parameters

|                                                                                  |                                |                                                        |
| -------------------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------ |
| [SDL_GPUCommandBuffer](SDL_GPUCommandBuffer) *                                   | **commandBuffer**              | a command buffer.                                      |
| [SDL_GPUStorageTextureWriteOnlyBinding](SDL_GPUStorageTextureWriteOnlyBinding) * | **storageTextureBindings**     | an array of writeable storage texture binding structs. |
| Uint32                                                                           | **storageTextureBindingCount** | the number of storage textures to bind from the array. |
| [SDL_GPUStorageBufferWriteOnlyBinding](SDL_GPUStorageBufferWriteOnlyBinding) *   | **storageBufferBindings**      | an array of writeable storage buffer binding structs.  |
| Uint32                                                                           | **storageBufferBindingCount**  | the number of storage buffers to bind from the array.  |

## Return Value

([SDL_GPUComputePass](SDL_GPUComputePass) *) Returns a compute pass handle.

## Remarks

A compute pass is defined by a set of texture subresources and buffers that
will be written to by compute pipelines. These textures and buffers must
have been created with the COMPUTE_STORAGE_WRITE bit. All operations
related to compute pipelines must take place inside of a compute pass. You
must not begin another compute pass, or a render pass or copy pass before
ending the compute pass.

A VERY IMPORTANT NOTE Textures and buffers bound as write-only MUST NOT be
read from during the compute pass. Doing so will result in undefined
behavior. If your compute work requires reading the output from a previous
dispatch, you MUST end the current compute pass and begin a new one before
you can safely access the data.

## Version

This function is available since SDL 3.0.0.

## See Also

- [SDL_EndGPUComputePass](SDL_EndGPUComputePass)

----
[CategoryAPI](CategoryAPI), [CategoryAPIFunction](CategoryAPIFunction), [CategoryGPU](CategoryGPU)
