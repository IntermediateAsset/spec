# Asset Exchange Specification

Asset Exchange will use (.ae) for default file extension. The name "Asset Exchange" may be changed until the spec is completed. The file will be binary not JSON/XML. This will make loading stage faster.

# Names Suggessions

* Asset Exchange
* Intermediate Asset Representation
* Intermediate Asset
* Asset Intermediate Representation
* Visual Intermediate Representation

# Expected Features

* Completely Binary format
* No JSON parsing, No XML Parsing, No text Parsing
* Fast to load, fast to export
* Strict file, strict spec description 
* Platform independent
* Universal Shader Language (https://github.com/UniversalShading/spec) for shading if shadeers will be used
* Universal Material (https://github.com/UniversalMaterial) for material definitions (maybe)
* READONLY binary and WRITE-Enabled binaries
* Fetatures in common formats will be supported (COLLADA, glTF, Obj, USD, STL, Alembic...)
* Layering maybe supported
* External references (data maybe embedded or stored externally as db), this all also help to provide layering like USD
* Extensions, exendible
* Optional Compression
* Asset + Scene description in modern way
* Audio support
* Open spec, open source

# Official Loader

[AssetKit](https://github.com/recp/AssetKit) will be the official loader but some alternative simple loader may be provieded if needed.

---

# Spec

Files are completely BINARY, and must start with start MAGIC number: `AE0F`.

- Little Endian is used, no option to store as Big Endian to make it strict. 
- Right Hand Rule is used
- All units are meters
- Default UP axis is Y-UP

Format:

```
| Header | AssetInfo | Sections Header | Sections | Embedded Data | EOF |
```

### 1. Header

```
4: uint32_t - Magic (AE0F)
4: uint32_t - Version
8: uint64_t - File Length
```

### 2. Sections Header

```
4: uint32_t - Sections Count
```

### 3. AssetInfo

```
1: uint8_t  - UP Axis
1: uint8_t  - Front face winding order (Default is counter-clockwise (CCW))
8: time_t   - created at (unix timestamp)
8: time_t   - modified at (unix timestamp)
```

Up Axis must be one of:

```
0: Y UP
1: Z UP
2: X UP
```

Winding order must be one of:

```
0: Counter-clockwise (CCW)
1: Clockwise (CW)
```

### 4. Sections

Sections are used to group specific types of elements like lights, cameras, nodes, scenes. A section provides section type which identifies itself.

```
| Type | Length | Section Content |
```

```
4: uint32_t  - Type
8: uint64_t  - Length
N: Section Content
```

Each section will define its own content definition separately.

Section Types:

```
0:  Unknown / Invalid
1:  Mesh Primitives
2:  Geometries
3:  Materials
4:  Effects
5:  Images
6:  Textures
7:  Samplers
8:  Scenes
9:  Lights
10: Cameras
11: Animations
...
```

## Sections

1. [Mesh Primitives](sections/mesh.prim.md)
2. [Geometries](sections/geometries.md)

