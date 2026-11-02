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

<div style="display: flex; align-items: center; justify-content: center; gap: 1.5rem; flex-wrap: wrap; margin: 1.5rem 0;">
  <img src="{{ "assets/img/projects/nudge_electrode.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 360px; width: auto;" data-zoomable>
  <img src="{{ "assets/img/projects/nudge_myoware.png" | relative_url }}" class="img-fluid rounded z-depth-1" style="height: 360px; width: auto;" data-zoomable>
</div>

I designed two 2-layer polyimide flex PCBs for EMG sensing. The first (left) is a custom electrode strip with 17 round electrode pads exposed on the skin side, routed to an onboard chip group and a single connector, with a hatched ground fill on the bottom layer and a stainless-steel stiffener under the components. The second (right) carries three MyoWare 2.0 sensors on stiffened sections separated by bend zones, so the board can curve around the forearm, with all three EMG channels broken out to one 5-pin connector. I also redesigned the original glove in CAD, replacing its enclosed design with a lightweight hex-cut frame and finger rings that guide the actuation cables.

<div style="margin: 1.5rem 0;">
  {% include figure.liquid path="assets/img/projects/nudge_schematic.png" class="img-fluid rounded z-depth-1" zoomable="true" caption="Main control board schematic: battery and charging, 9V boost, DRV8833 motor driver, XIAO ESP32-S3, EMG/FSR sensor inputs, and motor/encoder connectors." %}
</div>

Check back later for more updates!