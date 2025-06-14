# GLFS Spec (v0)
_**g**ood **l**ittle **f**ile **s**ystem, version 0_

(affectionately _**g**ood **l**uck **f**ile **s**ystem, version 0_)

## GLFS Structure Overview
```
[sector 0] GLFS SUPERBLOCK
----------
- magic GLFS+version identifier

[sector 1+] DIRECTORY TABLE
-----------
     [entry 0] filename: string
               start sector: int
	       size: int (bytes)

     [entry 1] filename: string
               start sector: int
	       size: int (bytes)
     (...)
     
[end of table marker]
----------
[file data]
(...)
```

### `[0]` Superblock Overview
- size: 512b
- contents:
     - bytes 0..7: `GLFSv0\n` (7 bytes+newline)
     - bytes 7..511: _reserved_

### `[sector 1+]` Directory Table Overview
- each 40-byte directory entry contains:
     - 32 byte filename
     - 4 byte (uint32) start sector (offset from sector 0)
     - 4 byte (uint32) file size in bytes
- end of table is marked with `b'__END__'` (8 bytes) 
