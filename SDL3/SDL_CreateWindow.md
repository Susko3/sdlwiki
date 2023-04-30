###### (This is the documentation for SDL3, which is under heavy development and the API is changing! [SDL2](https://wiki.libsdl.org/SDL2/) is the current stable version!)
# SDL_CreateWindow

Create a window with the specified dimensions and flags.

## Syntax

```c
SDL_Window* SDL_CreateWindow(const char *title, int w, int h, Uint32 flags);

```

## Function Parameters

|               |                                                                    |
| ------------- | ------------------------------------------------------------------ |
| **title**     | the title of the window, in UTF-8 encoding                         |
| **w**         | the width of the window, in screen coordinates                     |
| **h**         | the height of the window, in screen coordinates                    |
| **flags**     | 0, or one or more [SDL_WindowFlags](SDL_WindowFlags) OR'd together |

## Return Value

Returns the window that was created or NULL on failure; call
[SDL_GetError](SDL_GetError)() for more information.

## Remarks

`flags` may be any of the following OR'd together:

- [`SDL_WINDOW_FULLSCREEN`](SDL_WINDOW_FULLSCREEN): fullscreen window at
  desktop resolution
- [`SDL_WINDOW_OPENGL`](SDL_WINDOW_OPENGL): window usable with an OpenGL
  context
- [`SDL_WINDOW_VULKAN`](SDL_WINDOW_VULKAN): window usable with a Vulkan
  instance
- [`SDL_WINDOW_METAL`](SDL_WINDOW_METAL): window usable with a Metal
  instance
- [`SDL_WINDOW_HIDDEN`](SDL_WINDOW_HIDDEN): window is not visible
- [`SDL_WINDOW_BORDERLESS`](SDL_WINDOW_BORDERLESS): no window decoration
- [`SDL_WINDOW_RESIZABLE`](SDL_WINDOW_RESIZABLE): window can be resized
- [`SDL_WINDOW_MINIMIZED`](SDL_WINDOW_MINIMIZED): window is minimized
- [`SDL_WINDOW_MAXIMIZED`](SDL_WINDOW_MAXIMIZED): window is maximized
- [`SDL_WINDOW_MOUSE_GRABBED`](SDL_WINDOW_MOUSE_GRABBED): window has
  grabbed mouse focus

The [SDL_Window](SDL_Window) is implicitly shown if
[SDL_WINDOW_HIDDEN](SDL_WINDOW_HIDDEN) is not set.

On Apple's macOS, you **must** set the NSHighResolutionCapable Info.plist
property to YES, otherwise you will not receive a High-DPI OpenGL canvas.

The window size in pixels may differ from its size in screen coordinates if
the window is on a high density display (one with an OS scaling factor).
Use [SDL_GetWindowSize](SDL_GetWindowSize)() to query the client area's
size in screen coordinates, and
[SDL_GetWindowSizeInPixels](SDL_GetWindowSizeInPixels)() or
[SDL_GetRenderOutputSize](SDL_GetRenderOutputSize)() to query the drawable
size in pixels. Note that the drawable size can vary after the window is
created and should be queried again if you get an
[SDL_EVENT_WINDOW_PIXEL_SIZE_CHANGED](SDL_EVENT_WINDOW_PIXEL_SIZE_CHANGED)
event.

If the window is set fullscreen, the width and height parameters `w` and
`h` will not be used. However, invalid size parameters (e.g. too large) may
still fail. Window size is actually limited to 16384 x 16384 for all
platforms at window creation.

If the window is created with any of the
[SDL_WINDOW_OPENGL](SDL_WINDOW_OPENGL) or
[SDL_WINDOW_VULKAN](SDL_WINDOW_VULKAN) flags, then the corresponding
LoadLibrary function ([SDL_GL_LoadLibrary](SDL_GL_LoadLibrary) or
[SDL_Vulkan_LoadLibrary](SDL_Vulkan_LoadLibrary)) is called and the
corresponding UnloadLibrary function is called by
[SDL_DestroyWindow](SDL_DestroyWindow)().

If [SDL_WINDOW_VULKAN](SDL_WINDOW_VULKAN) is specified and there isn't a
working Vulkan driver, [SDL_CreateWindow](SDL_CreateWindow)() will fail
because [SDL_Vulkan_LoadLibrary](SDL_Vulkan_LoadLibrary)() will fail.

If [SDL_WINDOW_METAL](SDL_WINDOW_METAL) is specified on an OS that does not
support Metal, [SDL_CreateWindow](SDL_CreateWindow)() will fail.

On non-Apple devices, SDL requires you to either not link to the Vulkan
loader or link to a dynamic library version. This limitation may be removed
in a future version of SDL.

## Version

This function is available since SDL 3.0.0.

## Code Examples

```c++
// Example program:
// Using SDL2 to create an application window

#include "SDL.h"
#include <stdio.h>

int main(int argc, char* argv[]) {

    SDL_Window *window;                    // Declare a pointer

    SDL_Init(SDL_INIT_VIDEO);              // Initialize SDL2

    // Create an application window with the following settings:
    window = SDL_CreateWindow(
        "An SDL2 window",                  // window title
        640,                               // width, in pixels
        480,                               // height, in pixels
        SDL_WINDOW_OPENGL                  // flags - see below
    );

    // Check that the window was successfully created
    if (window == NULL) {
        // In the case that the window could not be made...
        printf("Could not create window: %s\n", SDL_GetError());
        return 1;
    }

    // The window is open: could enter program loop here (see SDL_PollEvent())

    SDL_Delay(3000);  // Pause execution for 3000 milliseconds, for example

    // Close and destroy the window
    SDL_DestroyWindow(window);

    // Clean up
    SDL_Quit();
    return 0;
}

```

## Related Functions

* [SDL_CreatePopupWindow](SDL_CreatePopupWindow)
* [SDL_CreateWindowFrom](SDL_CreateWindowFrom)
* [SDL_CreateWindowWithPosition](SDL_CreateWindowWithPosition)
* [SDL_DestroyWindow](SDL_DestroyWindow)

----
[CategoryAPI](CategoryAPI), [CategoryVideo](CategoryVideo)

