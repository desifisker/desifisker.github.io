---
layout: page
title: Virtual Teach and Repeat
description: Aerial imagery and digital-twin scene reconstructions for zero-shot ground vehicle navigation.
img: assets/img/publication_preview/thesis.jpg
importance: 0
category: research
permalink: /projects/virtual-teach-repeat/
---

Virtual Teach and Repeat (VirT&R) extends Teach and Repeat navigation by replacing the physical teach pass with a virtual one. A UAV captures imagery of the target environment, a scene reconstruction is built from that imagery, and a UGV path is piloted in simulation before the real vehicle enters the environment.

The resulting virtual route is converted into a teach map with point-cloud submaps, enabling the UGV to localize against the generated map and autonomously repeat the mission in the real world.

## Highlights

- Developed and evaluated a virtual teaching pipeline for GPS-denied autonomous ground vehicle navigation.
- Used UAV imagery, NeRF-based scene reconstruction, simulated UGV piloting, and LiDAR Teach and Repeat.
- Demonstrated smooth closed-loop path tracking over more than 12 km in the IROS paper and more than 33 km across the broader thesis experiments.
- Compared performance against conventional LiDAR Teach and Repeat using measured path-tracking error.

## Documents

- [IROS 2025 paper](/assets/pdf/fisker-uav-see-ugv-do-iros-2025.pdf)
- [MASc thesis](https://utoronto.scholaris.ca/items/f8efadbf-afb8-46e9-97be-72551ae875c0)

## Media and Code

- Image: add project images under `assets/img/projects/virtual-teach-repeat/`.
- Code: add repository links here when ready.
