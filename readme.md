# GLFS Spec (v0)
***g**ood **l**uck **f**ile **s**ystem, version 0*


## GLFS Structure
```
[sector 0] GLFS  SUPERBLOCK
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

[file data]
(...)

[end of disk marker]
```
