###### (This function is part of SDL_ttf, a separate library from SDL.)
# TTF_FontAscent

Query the offset from the baseline to the top of a font.

## Header File

Defined in SDL_ttf.h

## Syntax

```c
int TTF_FontAscent(const TTF_Font *font);

```

## Function Parameters

|              |                    |
| ------------ | ------------------ |
| **font**     | the font to query. |

## Return Value

Returns the font's ascent.

## Remarks

This is a positive value, relative to the baseline.

## Version

This function is available since SDL_ttf 3.0.0.

----
[CategoryAPI](CategoryAPI), [CategoryAPIFunction](CategoryAPIFunction)

