# CAD models

3D scan and CAD model files maintained in Git LFS.

## Unitree G1

This directory contains a reverse-engineered 3D model of the Unitree G1. The
model was reverse engineered using a Creality Sermoon S1 3D scanner.

### Files

| File | Format | Description |
| --- | --- | --- |
| `unitree-g1/unitree-g1.asc` | ASC | ASCII point data export |
| `unitree-g1/unitree-g1.obj` | OBJ | ASCII polygon mesh, suitable for importing into most 3D applications |
| `unitree-g1/unitree-g1.ply` | PLY | Binary polygon mesh |
| `unitree-g1/unitree-g1.stl` | STL | STL mesh for common 3D printing and CAD workflows |

All Unitree G1 files are stored with Git LFS because of their size. Install
[Git LFS](https://git-lfs.com/) before cloning or pulling the repository:

```sh
git lfs install
git clone git@github.com:MOBILAB-UDESC/cad-models.git
```
