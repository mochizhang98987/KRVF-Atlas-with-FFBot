# Voxel Manipulator

**A ROS 2 robot world model for embodied AI, VLA, semantic voxel memory, and language-guided mobile manipulation.**

![ROS 2](https://img.shields.io/badge/ROS%202-Jazzy-22314E)
![Gazebo](https://img.shields.io/badge/Sim-Gazebo-orange)
![Embodied AI](https://img.shields.io/badge/Embodied%20AI-VLA%20%2B%20World%20Model-purple)
![Status](https://img.shields.io/badge/Code-private%20until%20Sep%202026-lightgrey)

Voxel Manipulator connects VLM/VLA reasoning with robot execution through a source-aware semantic voxel world. It grounds language and image-space detections into RGB-D + TF-backed 3D evidence, stores objects and grasp candidates in semantic voxels, and uses spatial action cells for memory, place context, and SLAM-like localization advice.

The system is currently **not open-source**. Public release is planned **after September 2026**.

## What it does

- Builds a queryable robot world model from RGB-D, TF, and semantic observations.
- Grounds VLM/VLA outputs into 3D voxel evidence.
- Stores objects, aliases, freshness, hypotheses, and grasp candidates in semantic voxels.
- Uses spatial action cells and keyframes for memory and place context.
- Routes known objects from memory to Nav2 and MoveIt 2.
- Searches for unknown targets with VLM, then grounds and grasps them.
- Keeps high-level AI away from direct actuator authority.

## Demo highlights

### VLA Force-Grasp

*See it. Pull it. Strike it.*

<p align="center">
  <img src="voxel-manipulator-doc/photos/force-grasp/force-grasp.gif" width="82%" alt="VLA force grasp demo">
</p>

### Spatial Memory Pick

*Known objects, routed and grasped across rooms.*

<p align="center">
  <img src="voxel-manipulator-doc/photos/spatial-memory-pick.gif" width="82%" alt="Spatial memory pick demo">
</p>

### Spatial Action Cells

*Voxel landmarks recover place context.*

<p align="center">
  <img src="voxel-manipulator-doc/photos/action-cells-localization/action-cells-localization.gif" width="82%" alt="Action cells localization demo">
</p>

### Zero-Prior VLM Hunt

*No YOLO. No prior map. Find, ground, grasp.*

<p align="center">
  <img src="voxel-manipulator-doc/photos/vlm-search/vlm-search.gif" width="82%" alt="Zero-prior VLM hunt demo">
</p>

## Runtime idea

```text
language task
-> spatial-memory query or VLM search
-> RGB-D / TF grounding
-> semantic voxel update
-> Nav2 approach
-> observation refresh
-> grasp validation
-> MoveIt 2 execution
```

Voxel Manipulator separates:

```text
semantic proposal != grounded world evidence != action authorization
```

That separation is the point: the VLM can propose, but the runtime decides whether the robot is allowed to move or grasp.

## Why it matters

Embodied AI needs more than recognition. A robot must remember what was seen, where it was grounded, whether it is still fresh, and whether it can support action. Voxel Manipulator turns VLM cognition into robot-usable world state.

## What questions this project explores

- How can VLM/VLA outputs become grounded robot world state?
- How can a mobile manipulator use semantic voxel memory for language-guided grasping?
- How can robot actions be gated by source, freshness, grounding, and geometric support?
- How can a robot search for an unknown object without YOLO or a prior object map?
- How can action cells provide SLAM-like spatial context for embodied AI systems?

## System stack

- **ROS 2 Jazzy**
- **Gazebo + RViz**
- **Semantic voxel world**
- **Spatial action cells / keyframes / object aliases**
- **Nav2** for mobile navigation
- **MoveIt 2** for arm execution
- **VLM/VLA planner** for language and visual search

## Keywords

Embodied AI, Vision-Language-Action, VLA, VLM, robot world model, semantic voxel mapping, semantic voxel memory, spatial memory, mobile manipulation, language-guided robotics, RGB-D grounding, ROS 2, Nav2, MoveIt 2, Gazebo, RViz.
