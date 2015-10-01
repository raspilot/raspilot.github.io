---
layout: page-fullwidth
title: "Onboard Compass soft-iron Calibration"
subheadline: "How to use RasPilot"
teaser: "The documentation is a work in progress..."
permalink: "/softiron_calibration/"
header: no
---

The big metal USB sockets on <strong>Raspberry Pi B+</strong> and <strong>Raspberry Pi 2 B</strong> can result in magentic field changed nearby the on-board compass sensor(soft-iron effect), leading to the X axis mag value collected by RasPilot is higher than that of Y axis & Z axis, and when calibrating the compass, the mag value points displayed on Mission Planner looks like a rugby, rather than a globe.

Fortunately, the latest ArduPilot code adds on the soft-iron calibration function. Before conducting the on-board compass calibration, you should update your <strong>Mission Planner</strong> to the latest <strong>BETA</strong> version.

To update your Mission Planner, click the <strong>"HELP"</strong> tab, then click <strong>"Check for BETA Updates"</strong> button on the bottom.

<img src="{{ site.url }}/images/pages_update_mp.png">
