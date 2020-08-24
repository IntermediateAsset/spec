# Asset Exchange Specification

Asset Exchange will use (.ae) for default file extension. The name "Asset Exchange" may be changed until the spec is completed. The file will be binary not JSON/XML. This will make loading stage faster.

# Binary Format

File must start with start MAGIC number: `AE0F`.

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
8: time_t   - created at (unix timestamp)
8: time_t   - modified at (unix timestamp)
```

Up Axis must be one of:

```
0: Y UP
1: Z UP
2: X UP
```

### 4. Sections

Sections are used to group specific types of elements like lights, cameras, nodes, scenes. A section provides section type which identifies itself.

```
| Type | Length | Section Content |
```

- **Type** is 4byte/32bit unsigned integer (uint32_t).
- **Length** is 8byte/64bit unsigned integer (uint64_t).

Each section will define its own content definition separately.

Section Types:

```
0:  Unknown / Invalid
1:  Geometries
2:  Materials
3:  Effects
4:  Images
5:  Textures
6:  Samplers
7:  Scenes
8:  Lights
9:  Cameras
10: Animations
...
```

## Sections

### Geometries



