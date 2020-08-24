# Asset Change Specification

Asset Change will use (.ae) for default file extension. The name "Asset Change" may be changed until the spec is completed. The file will be binary not JSON/XML. This will make loading stage faster.

# Binary Format

File must start with start MAGIC number: `AE0F`.

Format:

```
| Header | AssetInfo | Sections | EOF |
```

### Header

```
4: uint32_t - Magic (AE0F)
4: uint32_t - Version
8: uint64_t - File Length
```
