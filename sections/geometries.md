
# Geometries Section

Spec allows two kind of geometries

1. Known Geometry Primitives (e.g. Box, Plane ...)
2. Geometries defined in the file exlicitly

A geometry definition is similar to other file formats.

```
4: uint32_t - Section Type == 2
8: uint64_t - Total Size of Geometry Entry
N: Geometry Definition
```

```
4: uint16_t - Geometry Type
N: Geometry Content
```

Geometry Types:

```
1: Mesh
2: Spline
3: Brep
```

---

1. [Mesh](geomety.mesh.md)
