# Flood Fill

## Description

Given an matriz A, imagine as if each element represents a pixel on the screen. If randomly selected a element change the color C of the element and all the surround elements with the same color.


## Resolutions
- Recursion
- BFS ()

### Recursion

```
// Base cases
if (x < 0 || x >= M ||
    y < 0 || y >= N)
    return;
if (screen[x, y] != prevC)
    return;

// Replace the color at (x, y)
screen[x, y] = newC;

floodFillUtil(screen, x + 1, y, prevC, newC);
floodFillUtil(screen, x - 1, y, prevC, newC);
floodFillUtil(screen, x, y + 1, prevC, newC);
floodFillUtil(screen, x, y - 1, prevC, newC);
```

## References
[Flood Fill]()