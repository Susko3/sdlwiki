###### (This is the documentation for SDL3, which is the current stable version. [SDL2](https://wiki.libsdl.org/SDL2/) was the previous version!)
# SDL_HINT_AUDIO_ALSA_DEFAULT_RECORDING_DEVICE

Specify the default ALSA audio recording device name.

## Header File

Defined in [<SDL3/SDL_hints.h>](https://github.com/libsdl-org/SDL/blob/main/include/SDL3/SDL_hints.h)

## Syntax

```c
#define SDL_HINT_AUDIO_ALSA_DEFAULT_RECORDING_DEVICE "SDL_AUDIO_ALSA_DEFAULT_RECORDING_DEVICE"
```

## Remarks

This variable is a specific audio device to open for recording, when the
"default" audio device is used.

If this hint isn't set, SDL will check
[SDL_HINT_AUDIO_ALSA_DEFAULT_DEVICE](SDL_HINT_AUDIO_ALSA_DEFAULT_DEVICE)
before choosing a reasonable default.

This hint should be set before an audio device is opened.

## Version

This hint is available since SDL 3.1.7.

## See Also

- [SDL_HINT_AUDIO_ALSA_DEFAULT_PLAYBACK_DEVICE](SDL_HINT_AUDIO_ALSA_DEFAULT_PLAYBACK_DEVICE)
- [SDL_HINT_AUDIO_ALSA_DEFAULT_DEVICE](SDL_HINT_AUDIO_ALSA_DEFAULT_DEVICE)

----
[CategoryAPI](CategoryAPI), [CategoryAPIMacro](CategoryAPIMacro), [CategoryHints](CategoryHints)
