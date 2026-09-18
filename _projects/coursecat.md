---
layout: page
title: CourseCat
description: A <strong>Canvas LMS AI companion app</strong> giving students a smarter, unified dashboard for assignments, grades, and schedule in one place.
importance: 2
category: projects
tags: [Web Dev, AI]
redirect: https://coursecat.org
# img: assets/img/projects/coursecat1.png
---

<div style="margin-bottom: 1.5rem;">
  <a href="https://coursecat.org" class="project-link-btn link-website" role="button">Website</a>
</div>

CourseCat is a third-party companion app for Canvas LMS that gives students a smarter, unified view of their assignments, grades, and schedule. It connects securely to a school's Canvas instance via API token, with optional Synergy/StudentVUE integration for schools using both systems.

The dashboard includes a color-coded assignment calendar with priority levels, due-date heatmaps, and alerts; a grade tracker with real-time monitoring and what-if score simulation for planning ahead; a unified assignment browser across all courses with submission status at a glance; and a modules and files explorer with inline file and PDF previews. Urgency is configurable rather than fixed — students set their own critical/high/medium thresholds by days-until-due and point value, so the calendar reflects how _they_ actually triage.

A standout feature is **ChatCat**, an AI companion built on the Vercel AI SDK that can walk through problems directly from uploaded course PDFs step-by-step, and reasons over a student's synced Canvas grade history to explain _why_ they're losing points on specific assignment types and what a given teacher tends to value.

Not everything a student needs lives in Canvas, so I added **profile entries**: a place to log teacher feedback, grade records, or study notes by typing them or photographing them. Uploaded photos of graded paper assignments run through text extraction, so handwritten comments and marked-up rubrics become editable, searchable text alongside everything Canvas already knows.

Users sign in with email/password or Google, and Canvas credentials are stored securely, while any Synergy credentials remain local-only. The app ships with account settings, dark mode, and an in-app feedback pipeline for user-reported issues.
