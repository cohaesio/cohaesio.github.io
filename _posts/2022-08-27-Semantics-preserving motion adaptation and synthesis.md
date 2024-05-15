---
layout:     post
title:      Semantics-preserving motion adaptation and synthesis
subtitle:   3D human scene interaction (HSI); motion parameterization and human motion synthesis
date:       2022-08-27
author:     Mingrui Zhang
header-img: img/ani-banner.png
catalog: true
tags:
    - Computer Animation
    - Computer Vision


---


# Human-Scene-Interaction

## Introduction

This study is focused on exploring the "semantics" of human motion with the aim of enabling it to generalize to new scenes. In computer graphics, 3D scenes are frequently reconstructed without human presence, making it a challenging task to synthesize realistic people in scenes, as well as recover humans in scenes. Automation of **human motion interaction (HSI)** can significantly reduce animation costs and create new possibilities in the AR industry. For instance, in a scenario where a human sits down on a chair, the character must automatically adjust its motion to accommodate the smaller chair. 

By studying the semantics of human motion, we can synthesize complex motions based on multiple simple motions. For instance, we could synthesize a human holding handrails while shrugging using three simple motions, such as standing, shrugging, and leaning. This is particularly useful because complex motions can be difficult to capture, whereas simple motions can be easily obtained online. Motion parameterization and synthesis has the potential to enable the spatial composition of high-quality human motion outcomes and significantly reduce the cost of motion capture. 

<table>
  <tr>
    <!-- Image 1 -->
    <td style="text-align: center;">
      <img src="img/ani-i1.png" alt="HSI examples" style="width: 100%; max-width: 300px;">
      <figcaption>HSI examples. People Sitting on different sized chairs.</figcaption>
    </td>
    <!-- Image 2 -->
    <td style="text-align: center;">
      <img src="img/ani-i2.png" alt="examples" style="width: 100%; max-width: 300px;">
      <figcaption>Examples of motion synthesis. (Standing Shrugging->Holding handrails Shrugging)</figcaption>
    </td>
  </tr>
</table>

## Related Works

<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Description</th>
      <th>Figure</th>
      <th>Limitations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Constraint-based motion synthesis</strong></td>
      <td>motion retargeting of dancing interactions based on positional constraint[2], avoid penetrations by using inequality constraints or a combination of collision detections and equality constraints [3, 4]</td>
      <td><img src="img/ani-r1.png" alt="Constraint-based synthesis" style="width:100%; max-width: 200px;"></td>
      <td><strong>Constraint based methods.</strong> Unable to represent implicit spatial relationship.</td>
    </tr>
    <tr>
      <td><strong>Character animation by spatial relationships</strong></td>
      <td>
        1. encoding neighborhood formations and individual trajectories as Laplacian coordinates[6].<br>
        2. Optimize the interaction mesh with pruning and normalization [7, 8]
      </td>
      <td>
        <img src="img/ani-r2.png" alt="Spatial relationships" style="width:100%; max-width: 200px;"><br>
        <img src="img/ani-r3.png" alt="Optimized interaction mesh" style="width:100%; max-width: 200px;">
      </td>
      <td>
        <strong>Skeleton-based methods.</strong> Unsuitable for capturing skin-level spatial relationships.<br>
        Unable to handle motion retargeting between different sized characters.
      </td>
    </tr>
  </tbody>
</table>

## Contributions

- Skin-level motion retargeting, robust to source and target characters from different dimensions
-  New representations of implicit spatial relationship
-  Enable characters to adapt to new scenes without additional training data

![examples](img/ani-o1.png)



![examples](img/ani-m0.png)

## Experiments



#### Same Character, Different Environment

| Examples (Click to view)                                     |
| ------------------------------------------------------------ |
| [**Exiting** **Car.** **Source** **motion** **in** **green** **and** **adapted** **motion** **in** **red.**](https://www.youtube.com/watch?v=ChwtiJH_kxs) |
| [**Typing.** **Source** **motion** **(left)** **and** **adapted** **motion** **(right).**](https://www.youtube.com/watch?v=-h9FlnuqqTI) |



#### Different Character, Same Environment

**Example**: **V-Tuber** **in** **a** **live** **room.** (The method has been applied into one [intelligent VTuber product](https://ai.kuaishou.com/technology/Solution/VirtualLive) by Kwai Technology.)

| Sample | Input Data                                                  | Naive Results                                                | Optimized Results                                            |
| ------ | ----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1      | [source motion](https://www.youtube.com/shorts/03UXyakbqEs) | [Retargeted(original)](https://www.youtube.com/watch?v=iClpQllxLVs) | [Retargeted(optimized)](https://www.youtube.com/watch?v=mliP0X2mKZA) |
| 2      | [source motion](https://www.youtube.com/shorts/pvPmi9INIlE) | [Retargeted(original)](https://www.youtube.com/watch?v=Bo3yYgoOtD8) | [Retargeted(optimized)](https://www.youtube.com/watch?v=WQ4dLA_UNXw) |
