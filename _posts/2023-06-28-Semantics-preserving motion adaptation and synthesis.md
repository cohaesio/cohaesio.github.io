---
layout:     post
title:      Semantics-preserving motion adaptation and synthesis
subtitle:   3D human scene interaction (HSI); motion parameterization and human motion synthesis
date:       2023-06-28
author:     Mingrui Zhang
header-img: img/ani-banner.png
catalog: true
tags:
    - Computer Animation
    - Computer Vision


---

<head>
    <link rel="stylesheet" href="{{ 'css/style.css' | relative_url }}">
</head>

This work is [published](https://dl.acm.org/doi/10.1145/3581783.3612218) at ACM Multimedia 2023.

# Human-Scene-Interaction

## Introduction

This study is focused on exploring the "semantics" of human motion with the aim of enabling it to generalize to new scenes. In computer graphics, 3D scenes are frequently reconstructed without human presence, making it a challenging task to synthesize realistic people in scenes, as well as recover humans in scenes. Automation of **human motion interaction (HSI)** can significantly reduce animation costs and create new possibilities in the AR industry. For instance, in a scenario where a human sits down on a chair, the character must automatically adjust its motion to accommodate the smaller chair.

By studying the semantics of human motion, we can synthesize complex motions based on multiple simple motions. For instance, we could synthesize a human holding handrails while shrugging using three simple motions, such as standing, shrugging, and leaning. This is particularly useful because complex motions can be difficult to capture, whereas simple motions can be easily obtained online. Motion parameterization and synthesis has the potential to enable the spatial composition of high-quality human motion outcomes and significantly reduce the cost of motion capture.

<table style="border-collapse: collapse; width: 100%;">
  <tr>
    <!-- Image 1 -->
    <td style="text-align: center; border: none;">
      <img src="img/ani-i1.png" alt="HSI examples" style="width: 100%; max-width: 300px;">
      <figcaption>HSI examples. People Sitting on different sized chairs.</figcaption>
    </td>
    <!-- Image 2 -->
    <td style="text-align: center; border: none;">
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

<img src="img/ani-o1.png" alt="examples" style="width: 40%;">


<img src="img/ani-m0.png" alt="examples" style="width: 80%;">

## Experiments


<div class="video-links">
    <h2>Same Character, Different Environment</h2>
    <ul>
        <li>

                <strong>Exiting Car.</strong> Source motion in green and adapted motion in red.
                <iframe width="373" height="210" src="https://www.youtube.com/embed/ChwtiJH_kxs?si=SHWOvM7wE5SL0smb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
        </li>
        <li>

                <strong>Typing.</strong> Source motion (left) and adapted motion (right).
                <iframe width="373" height="210" src="https://www.youtube.com/embed/-h9FlnuqqTI?si=fY09X_3wTOjJ7TsY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

        </li>
    </ul>
</div>



<div class="example-section">
    <h2>Different Character, Same Environment</h2>
    <p>The method has been applied into one <a href="https://ai.kuaishou.com/technology/Solution/VirtualLive" target="_blank">intelligent VTuber product</a> by Kwai Technology.</p>
    <table>
        <thead>
            <tr>
                <th>Sample</th>
                <th>Source Motion</th>
                <th>Naive Results</th>
                <th>Optimized Results</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Sample 1</td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/03UXyakbqEs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/iClpQllxLVs?si=BJ6xiwywncVJ5j7B" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/mliP0X2mKZA?si=e2bc_wXGHiqjBk_g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
            </tr>
            <tr>
                <td>Sample 2</td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/pvPmi9INIlE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/Bo3yYgoOtD8?si=w7Qwjx3yGN8gXAFx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
                <td>
                    <iframe width="186" height="105" src="https://www.youtube.com/embed/WQ4dLA_UNXw?si=d1-3E3N-l_hjo_Sw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                </td>
            </tr>
        </tbody>
    </table>
</div>
