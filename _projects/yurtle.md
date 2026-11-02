---
layout: page
title: Yurtle
description: Robot built for 'Into the Deep' 24-25 competition for FIRST Tech Challenge. Reached playoffs at <strong>Chesapeake Championship</strong> and selected for <strong>national robotics premier event.</strong>
importance: 7
category: projects
tags: [Robotics]
# img: assets/img/projects/gg11.png
images:
  slider: true
---

Yurtle is FTC 24158 Green Gang's robot for the 2024–25 _Into the Deep_ season. I was a member of the software team, so this page covers the robot's code.

The centerpiece of our software is a **Finite State Machine** inspired by the Roadrunner library, used for both teleop and autonomous. In teleop, the FSM encapsulates robot state to simplify and automate subsystem transitions, scoring, transferring, and intaking all trigger automatically from a single button press. In autonomous, FSM-based state tracking lets us repeat movements and build in failsafes if any path segment goes wrong.

<div class="row mt-3 mb-3 justify-content-center">
  <div class="col-sm-7">
    {% include figure.liquid path="assets/img/projects/gg8.png" class="img-fluid rounded z-depth-1" zoomable="true" %}
  </div>
</div>

To handle a 5-subsystem transfer sequence, I implemented a **Java Commands framework** that chains subsystem methods simultaneously or sequentially, abstracting all individual movements behind one driver input.

<div class="row mt-3 mb-3 justify-content-center">
  <div class="col-sm-4">
    {% include figure.liquid path="assets/img/projects/gg9.png" class="img-fluid rounded z-depth-1" zoomable="true" %}
  </div>
</div>

Subsystem precision is handled through **PID control** on the intake arm and **motion profiling** on high-DOF subsystems, preventing robot tipping at full vertical extension and enabling smoother, faster cycles. For localization, we use **Pinpoint odometry,** switched from two-pod dead wheel tracking before Michiana for its faster refresh rate and more accurate IMU fusion. Autonomous paths are built with **Road Runner spline trajectories** for continuous, smooth movement with full control over position and heading throughout each segment.

<div style="display: flex; align-items: center; gap: 0.5rem; max-width: 60%; margin: 1rem auto;">
  <button onclick="document.getElementById('yurtleSlider').swiper.slidePrev()" style="background: none; border: 1px solid #ccc; border-radius: 50%; width: 2.2rem; height: 2.2rem; font-size: 1.3rem; cursor: pointer; color: #555; flex-shrink: 0; display: flex; align-items: center; justify-content: center;">&#8249;</button>
  <swiper-container id="yurtleSlider" keyboard="true" pagination="true" pagination-clickable="true" loop="true" centered-slides="true" style="flex: 1; min-width: 0;">
    <swiper-slide>
      <video class="img-fluid rounded z-depth-1" controls style="width: 100%;">
        <source src="{{ "/assets/img/projects/gg1.mp4" | relative_url }}" type="video/mp4">
      </video>
    </swiper-slide>
    <swiper-slide>
      <video class="img-fluid rounded z-depth-1" controls style="width: 100%;">
        <source src="{{ "/assets/img/projects/gg3.mp4" | relative_url }}" type="video/mp4">
      </video>
    </swiper-slide>
    <swiper-slide>
      <video class="img-fluid rounded z-depth-1" controls style="width: 100%;">
        <source src="{{ "/assets/img/projects/gg4.mp4" | relative_url }}" type="video/mp4">
      </video>
    </swiper-slide>
    <swiper-slide>
      <video class="img-fluid rounded z-depth-1" controls style="width: 100%;">
        <source src="{{ "/assets/img/projects/gg7.mp4" | relative_url }}" type="video/mp4">
      </video>
    </swiper-slide>
  </swiper-container>
  <button onclick="document.getElementById('yurtleSlider').swiper.slideNext()" style="background: none; border: 1px solid #ccc; border-radius: 50%; width: 2.2rem; height: 2.2rem; font-size: 1.3rem; cursor: pointer; color: #555; flex-shrink: 0; display: flex; align-items: center; justify-content: center;">&#8250;</button>
</div>
