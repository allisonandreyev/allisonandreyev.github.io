---
layout: page
title: NASA RL Sim
description: <strong>Reinforcement learning simulator</strong> for NASA Goddard's CORTEx terrain-adaptive navigation project, training and visualizing a CMAC/TD3 rover-navigation agent in real time.
importance: 5
category: research
tags: [Robotics, AI]
# img: assets/img/projects/recents/nasarl-sim-live.png
---

<div class="row mt-3 mb-3 justify-content-center">
  <div class="col-sm-5">
    {% include figure.liquid path="assets/img/projects/recents/nasarl-sim-live.png" class="img-fluid rounded z-depth-1" zoomable="true" %}
  </div>
</div>

_Completed August 2026 and presented at the NASA Goddard Engineering and Technology Directorate branch presentation and the National Space Club poster session._

This is a NASA Goddard Space Flight Center internship project (Engineering and Technology Directorate, Code 525 Space Club), now formalized as **CORTEx** (Cross-sensor Onboard Reflex & Terrain Exploration), building an RL-driven autonomous navigation system for the TurtleBot 4 that can handle diverse, unstructured terrain. The team split into three subteams: RL agent implementation, simulation development, and environment/sensing; I worked on the RL agent and owned the training simulator, and later designed the terrain-classification system.

I built a MATLAB-based training simulator with a live GUI: a customizable obstacle library (polygonal, square, and circular obstacles), randomized room shapes and boundary generation, and both static and dynamic (moving) obstacles. Simulated lidar renders as a full-circle ray fan around the rover, matching the real TurtleBot 4's scan geometry so trained agents transfer to hardware. 

Over the course of development I tightened the safety and physics fidelity of the sim: restricting lidar range to a realistic 12m, preventing obstacles from spawning inside the goal pose, adding a soft safety-region penalty around obstacles distinct from the collision penalty, and smoothing acceleration/deceleration so velocity commands ramp instead of jumping instantaneously. I also added path-trail visualization (a solid line for the current episode, dotted for the previous one) to make training behavior easier to inspect at a glance.

<div class="row mt-3 mb-3 justify-content-center">
  <div class="col-sm-9">
    {% include figure.liquid path="assets/img/projects/recents/nasarl-arrival-rate.png" class="img-fluid rounded z-depth-1" zoomable="true" %}
  </div>
</div>

The other half of my team's work was the supplemental sensing layer: an HDC-based artificial immune system paired with a camera-free terrain classifier. Sensor readings are random-projected into 10,000-dimensional hypervectors and bundled into a "memory of healthy" — 54,000+ readings compressed into 88 KB, roughly 1,700x smaller than a comparable ResNet-101-class classifier. Live readings are compared against that memory to isolate sensor faults, separate internal robot state from external environment changes, and classify the terrain with no camera and no ground-truth labels.

<div style="display: flex; align-items: center; justify-content: center; gap: 1.5rem; flex-wrap: wrap; margin: 1.5rem 0;">
  <img src="{{ "assets/img/projects/recents/nasarl-terrain-accuracy.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 280px; width: auto;" data-zoomable>
  <img src="{{ "assets/img/projects/recents/nasarl-hdc-similarity.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 280px; width: auto;" data-zoomable>
</div>

The final poster:

<div class="row mt-3 mb-3 justify-content-center">
  <div class="col-sm-11">
    {% include figure.liquid path="assets/img/projects/recents/nasarl-cortex-poster.png" class="img-fluid rounded z-depth-1" zoomable="true" %}
  </div>
</div>
