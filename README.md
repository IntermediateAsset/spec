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
| Header | AssetInfo | Sections | EOF |
```

### 1. Header

```
4: uint32_t - Magic (AE0F)
4: uint32_t - Version
8: uint64_t - File Length
```

### 2. AssetInfo

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

