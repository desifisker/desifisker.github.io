---
layout: page
title: Autonomous UAV Navigation
description: GNSS-denied UAV localization with satellite imagery, inverse NeRF methods, and real image-pose datasets.
importance: 2
category: research
permalink: /projects/autonomous-uav-navigation/
---

This project explored autonomous UAV localization below 30 m AGL without GNSS by comparing real onboard imagery against synthetic views and scene representations built from satellite-derived imagery.

## Tools

- Google Earth Studio
- VICON
- Instant-NGP
- Colmap
- Pi-NeRF

## Highlights

- Adapted invertible neural network and Mip-NeRF implementations for novel image pose estimation.
- Created image-pose pair datasets by tracking multiple reference frames with a stereo camera in a VICON lab.
- Evaluated Google Earth 3D renders against real imagery using SIFT, SURF, ORB, and SuperPoint feature matching.
- Focused on pose recovery for low-altitude UAV flight in GNSS-denied environments.
