
# Mesh Primitives Section

```
4: uint32_t - Section Type == 1
4: uint8_t  - Count
8: uint64_t - Total Size of Mesh Primitive Section
N: Mesh Primitive Definition
```

### Mesh Primitive

```
2:  uint16_t   - Primitive Type
1:  uint8_t    - Front face winding order (Default is counter-clockwise (CCW))
1:  uint8_t    - Cull Mode (Default is Back)
8:  uint64_t   - Depth State Index / Pointer (Default: NULL / 0, DepthState object which keeps writeEnabled, depthFunction...)
8:  uint64_t   - Material Index / Pointer
4:  uint16_t   - Input/Attrib Count
12: float32[3] - AABB Min
12: float32[3] - AABB Max
8:  uint64_t   - Indices Index / Pointer (Accessor)
N:  Attribs
```

Primitive Types:

```
0: Points

1: Triangles
2: Triangle Fans
3: Triangle Strips

4: Lines
5: Line Loop
6: Line Strip

7: Polylist
8: Polygons
```

Cull mode:

```
0: Undefined
1: Cull Back
2: Cull Front
3: Cull Is Disabled
```
