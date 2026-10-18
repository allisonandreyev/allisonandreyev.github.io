---
layout: page
title: Nudge
description: A lightweight <strong>EMG-controlled assistive glove</strong> that helps people with <strong>ALS</strong> grip and release objects using their own muscle signals.
importance: 2
category: projects
tags: [Hardware, PCB Design, Assistive Tech]
# img: assets/img/projects/nudge_glove.png
---

<div style="margin: 1.5rem 0;">
  {% include figure.liquid path="assets/img/projects/nudge_glove.png" class="img-fluid rounded z-depth-1" zoomable="true" caption="Glove frame CAD: a hex-cut back-of-hand plate with ring guides along each finger for the actuation cables." %}
</div>

Nudge is a fall internship project with UMD Cyber-Physical Systems Engineering (CPSE), building a soft assistive glove for people with ALS. A surface EMG sensor on the forearm picks up the wearer's muscle activity, and a wrist-mounted pod drives small motors that pull cables to close the thumb and index finger, so a weak flex is enough to grip and release everyday objects. I'm rebuilding Nudge from an earlier version developed by a team in CPSE's 2026 summer program, redesigning the glove and designing new PCBs for it.

The system runs on a XIAO ESP32-S3 with a DRV8833 driver powering two N20 gear motors with encoders. MyoWare 2.0 boards handle EMG sensing, force-sensing resistors on the thumb and index finger measure grip force, and a single-cell 1200 mAh LiPo with a micro-LiPo charger and 9V step-up regulator powers everything. Cables run through PTFE tubing, and a latex tube acts as a spring return to reopen the hand. Weight is the main design constraint: people with ALS can't carry heavy devices for hours, so the goal is a wrist housing under 175 g.

<div style="display: flex; align-items: center; justify-content: center; gap: 1.5rem; flex-wrap: wrap; margin: 1.5rem 0;">
  <img src="{{ "assets/img/projects/nudge_electrode.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 360px; width: auto;" data-zoomable>
  <img src="{{ "assets/img/projects/nudge_myoware.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 360px; width: auto;" data-zoomable>
</div>

I designed two 2-layer polyimide flex PCBs for EMG sensing. The first (left) is a custom electrode strip with 17 round electrode pads exposed on the skin side, routed to an onboard chip group and a single connector, with a hatched ground fill on the bottom layer and a stainless-steel stiffener under the components. The second (right) carries three MyoWare 2.0 sensors on stiffened sections separated by bend zones, so the board can curve around the forearm, with all three EMG channels broken out to one 5-pin connector. I also redesigned the original glove in CAD, replacing its enclosed design with a lightweight hex-cut frame and finger rings that guide the actuation cables.

<div style="margin: 1.5rem 0;">
  {% include figure.liquid path="assets/img/projects/nudge_schematic.png" class="img-fluid rounded z-depth-1" zoomable="true" caption="Main control board schematic: battery and charging, 9V boost, DRV8833 motor driver, XIAO ESP32-S3, EMG/FSR sensor inputs, and motor/encoder connectors." %}
</div>

The firmware has strict safety rules. Every motor command passes through one function that caps PWM at 70% and only lets one motor run at a time. The firmware cuts power within 300 ms if the encoders show a stall, never closes past the calibrated end stops, and resets through a watchdog if the code hangs. To filter out tremors, the wearer has to hold a flex for 250 ms to close the hand, and EMG input is ignored while a motor is running. Closing stops once the FSRs read the target grip force, which is 10–20 N depending on calibration. When the battery drops below 3.5 V, the hand opens itself before shutting down.
