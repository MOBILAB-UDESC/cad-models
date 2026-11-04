# CAD models

3D scan and CAD model files maintained in Git LFS.

```sh
git lfs install
git clone git@github.com:MOBILAB-UDESC/cad-models.git
cd cad-models
git lfs pull
```

## Unitree G1 back

This directory contains the 3D model of the Unitree G1 back. The
model was reverse engineered using a Creality Sermoon S1 3D scanner.

* `unitree-g1/reverse-engineered/unitree-g1-back-reverse-engineered.obj`
* `unitree-g1/reverse-engineered/unitree-g1-back-reverse-engineered.ply`
* `unitree-g1/reverse-engineered/unitree-g1-back-reverse-engineered.stl`

![Unitree G1 reverse-engineered model preview](unitree-g1/reverse-engineered/unitree-g1-back-reverse-engineered.png)

## Unitree G1 wrist RealSense D405 mount

Wrist camera mounts for attaching Intel RealSense D405 cameras to the
Unitree G1 wrists (M4010 wrist motor, Dex3-1 hand). These are the
original SolidWorks STEP exports published by Unitree in the
[unitreerobotics/xr_teleoperate](https://github.com/unitreerobotics/xr_teleoperate)
repository; see its
[Device.md](https://github.com/unitreerobotics/xr_teleoperate/blob/main/Device.md)
(section *G1 Wrist RealSense D405*) for the bill of materials and
fasteners (4x M3 hex nut, 4x M3x12 screw, 4x M3x6 screw).

| File | Part | Qty | Original file |
| --- | --- | --- | --- |
| `unitree-g1/d405-wrist-mount/unitree-g1-d405-wrist-mount-left.step` | Left wrist camera mount | 1 | [`right_wrist_D405_camera_mount.STEP`](https://github.com/unitreerobotics/xr_teleoperate/blob/7cd188c1657ad4df97cfcd44e9f35bac937f7f2b/hardware/right_wrist_D405_camera_mount.STEP) |
| `unitree-g1/d405-wrist-mount/unitree-g1-d405-wrist-mount-right.step` | Right wrist camera mount | 1 | [`wrist_ring_mount.STEP`](https://github.com/unitreerobotics/xr_teleoperate/blob/7cd188c1657ad4df97cfcd44e9f35bac937f7f2b/hardware/wrist_ring_mount.STEP) |
| `unitree-g1/d405-wrist-mount/unitree-g1-d405-wrist-ring-clamp.step` | Wrist ring clamp | 2 | [`left_wrist_D405_camera_mount.STEP`](https://github.com/unitreerobotics/xr_teleoperate/blob/7cd188c1657ad4df97cfcd44e9f35bac937f7f2b/hardware/left_wrist_D405_camera_mount.STEP) |

The upstream file names do not match their contents (the links in
`Device.md` are shifted by one row), so the files were renamed here to
describe the actual part. The left and right mounts are mirror images
of each other.

![Unitree G1 D405 wrist mount preview](unitree-g1/d405-wrist-mount/unitree-g1-d405-wrist-mount.png)

## Unitree G1 wrist RealSense D405 mount (5010 wrist)

Adaptation of the mount above for the newer G1 arm with the 5010 wrist
(the `*_5010.STL` wrist links in
[unitree_ros](https://github.com/unitreerobotics/unitree_ros/tree/master/robots/g1_description),
used by the `g1_29dof_mode_15/16/18` URDFs). The original mount clamps
onto the wrist yaw housing next to the hand, which on the M4010 wrist is
a ~Ø61 mm circle with one flat. On the 5010 wrist that housing has flats
on both sides and a fuller top cap, so the original ring does not seat.

Only the wrist bore changed: the clamping band and the bracket's top
saddle are re-cut to the 5010 housing outline plus 0.25 mm radial
clearance, and the band gains the second flat. The camera box, tab
positions, fasteners and part placement are unchanged, so the camera
sits in the same position relative to the hand.

| File | Part | Qty |
| --- | --- | --- |
| `unitree-g1/d405-wrist-mount-5010/unitree-g1-d405-wrist-mount-5010-left.step` | Left wrist camera mount | 1 |
| `unitree-g1/d405-wrist-mount-5010/unitree-g1-d405-wrist-mount-5010-right.step` | Right wrist camera mount | 1 |
| `unitree-g1/d405-wrist-mount-5010/unitree-g1-d405-wrist-ring-clamp-5010.step` | Wrist ring clamp | 2 |

Each part also has a `.stl` for printing. The bore was traced from the
URDF mesh, which is an approximation of the real
housing, so print one clamp first and test the fit. To change the
clearance, regenerate the parts with
`unitree-g1/d405-wrist-mount-5010/adapt_5010.py` (needs `build123d`,
`trimesh` and `numpy`):

```sh
cd unitree-g1/d405-wrist-mount-5010
python adapt_5010.py ../d405-wrist-mount . 0.4   # clearance in mm
```

![Unitree G1 D405 wrist mount for the 5010 wrist preview](unitree-g1/d405-wrist-mount-5010/unitree-g1-d405-wrist-mount-5010.png)
