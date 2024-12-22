###### (This is the documentation for SDL3, which is the current stable version. [SDL2](https://wiki.libsdl.org/SDL2/) was the previous version!)
# SDL_RenderDebugTextFormat

Draw debug text to an [SDL_Renderer](SDL_Renderer).

## Header File

Defined in [<SDL3/SDL_render.h>](https://github.com/libsdl-org/SDL/blob/main/include/SDL3/SDL_render.h)

## Syntax

```c
bool SDL_RenderDebugTextFormat(SDL_Renderer *renderer, float x, float y, const char *fmt, ...);
```

## Function Parameters

|                                |              |                                                                      |
| ------------------------------ | ------------ | -------------------------------------------------------------------- |
| [SDL_Renderer](SDL_Renderer) * | **renderer** | the renderer which should draw the text.                             |
| float                          | **x**        | the x coordinate where the top-left corner of the text will draw.    |
| float                          | **y**        | the y coordinate where the top-left corner of the text will draw.    |
| const char *                   | **fmt**      | the format string to draw.                                           |
| ...                            | **...**      | additional parameters matching % tokens in the `fmt` string, if any. |

## Return Value

(bool) Returns true on success or false on failure; call
[SDL_GetError](SDL_GetError)() for more information.

## Remarks

This function will render a printf()-style format string to a renderer.
Note that this is a convinence function for debugging, with severe
limitations, and is not intended to be used for production apps and games.

For the full list of limitations and other useful information, see
[SDL_RenderDebugText](SDL_RenderDebugText).

## Thread Safety

This function should only be called on the main thread.

## Version

This function is available since SDL 3.2.0.

## See Also

- [SDL_RenderDebugText](SDL_RenderDebugText)
- [SDL_DEBUG_TEXT_FONT_CHARACTER_SIZE](SDL_DEBUG_TEXT_FONT_CHARACTER_SIZE)

----
[CategoryAPI](CategoryAPI), [CategoryAPIFunction](CategoryAPIFunction), [CategoryRender](CategoryRender)
