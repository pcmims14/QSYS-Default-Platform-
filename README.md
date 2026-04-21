Q-SYS Default Conference Room Template

Baseline UCI + Gain Auto-Mute + Shared Camera Control + Platform CSS Themes

Overview

This repository contains a Q-SYS Designer baseline template built to accelerate conference room control system development.

It provides a reusable starting point that includes:

A prebuilt UCI navigation framework
A gain auto-mute utility with dynamic detection
A meter popup behavior for gain interaction
A shared multi-camera control framework
A selectable CSS theme system (Teams / Google Meet / Zoom + Light/Dark modes)

This is a programming template, not a fully integrated AV system.

What Makes This Useful

This file eliminates the repetitive setup you do on every job:

building a UCI from scratch
wiring up gain controls
mapping camera control buttons
styling interfaces per platform

Instead, you start with a working shell and adapt it.

Features
UCI Navigation Framework
Multi-layer navigation (Audio / Video / Camera / Help)
Interlocked navigation buttons
Dynamic legends via UCI variables
Centralized config for:
Page name
Layer names
Default layer
Button mappings

Behavior:

Only one content layer visible at a time
Invalid selections fall back to Home
Easily expandable via config table
Gain Auto-Mute Utility

Automatically detects compatible gain components and applies logic.

Detection Requirements:

gain
stepper.increase
stepper.decrease
stepper.time

Behavior:

Auto-populates:
Controls.gainList
Controls.gainButtons
Dynamically assigns event handlers
Applies threshold-based mute logic:
Gain ≤ threshold → Mute ON
Gain > threshold → Mute OFF
Button disabled → Force unmute

Use Case:
Quickly expose gain controls without manually mapping every component.

Meter Popup Behavior

Provides temporary visibility for gain feedback.

Behavior:

Press gain stepper → Meter shows instantly
Release → Timer starts
After delay → Meter hides

Configurable:

HIDE_AFTER = 1.0
Shared Camera Control Framework

A reusable structure for controlling multiple third-party cameras using a single UCI control set.

Camera System Design
Manual Camera Registration

Cameras are explicitly defined in script:

local C1 = Component.New("cam1")
local C2 = Component.New("cam2")

camTable = { C1, C2 }

Cameras are not auto-discovered. Add them manually.

Shared Control Mapping

The selected camera is dynamically bound to a shared control map:

Pan Up / Down / Left / Right
Zoom In / Out
Presets (1–3)

All UI buttons control only the active camera.

Camera Selection
Controlled via Controls.whichCamera
Interlocked selection
Rebinds control map on change
Clears active states during switching
Tracking Mode

Each camera maintains independent tracking state.

Controls:

cameraTrack[1] → Tracking ON
cameraTrack[2] → Tracking OFF

Behavior:

Tracking ON:
Enables camera auto-tracking
Hides manual controls
Tracking OFF:
Restores manual PTZ controls
UCI Expectations
Controls.whichCamera → one per camera
Controls.cameraControls → matches control map order
Plugin control names must match script exactly
CSS Theme System (Teams / Google Meet / Zoom)
Overview

The template includes a selectable CSS theme system that allows you to quickly match the UCI to common conferencing platforms.

Available Modes
Microsoft Teams style
Google Meet style
Zoom style
Light / Dark variations
Behavior
A selectable option at the top of the interface switches the theme
Updates styling across the UCI dynamically
Allows fast alignment with customer environment or platform preference
Why This Matters

This saves time on every job:

No rebuilding UI styles per project
No reworking colors to match platform standards
Faster client acceptance (familiar look/feel)
What This Template Does NOT Do

This is intentional:

No video routing logic
No source switching
No display control
No codec integration
No automatic camera discovery
No finalized DSP tuning

This is a foundation, not a finished system.

How to Use
1. Duplicate the Template

Start each project from a copy.

2. Configure UCI

Update:

Page names
Layer names
Labels
Theme defaults (if needed)
3. Validate Gain Components

Ensure gain blocks include:

gain
mute
stepper controls
4. Add Cameras
Create plugin components
Name them consistently (cam1, cam2, etc.)
Add to camTable
Match control names
5. Expand Per Project

Add:

Routing logic
Display control
Codec integration
Automation logic
Script Modules
UCI Navigation
Layer switching
Interlock behavior
Legend syncing
Gain Auto-Mute
Detection
Mapping
Threshold mute logic
Meter Popup
Temporary UI feedback
Timer-based visibility
Camera Control
Multi-camera selection
Shared control mapping
Tracking state handling
CSS Theme System
Platform-based UI styling
Light/Dark modes
Runtime switching
Best Practices
Keep naming consistent
Do not rely on auto-discovery for cameras
Keep control arrays aligned with script
Validate plugin control names
Avoid hardcoding values everywhere
Design Philosophy

Build once. Reuse everywhere.

This template focuses on:

Speed of deployment
Consistency across rooms
Maintainable scripting
Real-world usability
Version

v1.1 – Added Platform CSS Theme System

Notes

This template handles the repetitive front-end work:

UCI structure
Navigation
Gain handling
Camera control
Platform styling

Everything else should be layered on top per project.
