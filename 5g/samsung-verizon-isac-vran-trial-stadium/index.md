# Samsung and Verizon Turn 5G Into Radar in Milestone Live ISAC Trial

> In a live stadium trial, Samsung and Verizon proved 5G networks can double as high-resolution radar, tracking crowds and objects without dedicated sensors.

By InnotechInsider Staff · 5G & Connectivity · Sep 19, 2026
Canonical URL: https://innotechinsider.com/5g/samsung-verizon-isac-vran-trial-stadium/

> **TL;DR**: Samsung and Verizon have successfully field-tested Integrated Sensing and Communication (ISAC) over a live virtualized RAN architecture, proving that standard cellular infrastructure can operate simultaneously as a gigabit data pipe and a distributed radar array.

For more than a century, wireless communications and radar systems have lived in separate engineering silos. One array of antennas was built to transmit data packets to receivers; another, completely distinct system beamed radio pulses into the sky to catch their reflections off solid surfaces.

This week, Samsung Electronics and Verizon demonstrated that the boundary between the two has officially collapsed.

Operating at a major international sports venue, the two companies completed a successful end-to-end trial of Integrated Sensing and Communication (ISAC) running over Verizon’s commercial-grade virtualized Radio Access Network (vRAN). By multiplexing radar sensing directly into operational cellular spectrum, the deployment tracked crowd bottlenecks, perimeter anomalies, and aerial drone vectors with sub-meter accuracy—all without deploying a single standalone radar unit, optical camera, or dedicated lidar sensor.

The trial marks the clearest signal yet that 5G-Advanced is fulfilling its promise as the bridge to 6G, converting passive telecommunications towers into active environmental perception engines.

![modern sports stadium seating bowl with cellular antenna masts mounted on lighting rig](https://images.unsplash.com/photo-1623051783741-b9bab2ef3933?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxtb2Rlcm4lMjBzcG9ydHMlMjBzdGFkaXVtJTIwc2VhdGluZyUyMGJvd2wlMjB3aXRoJTIwY2VsbHVsYXIlMjBhbnRlbm5hJTIwbWFzdHMlMjBtb3VudGVkJTIwb24lMjBsaWdodGluZyUyMHJpZ3xlbnwwfDB8fHwxNzg5ODExODQ1fDA&ixlib=rb-4.1.0 "modern sports stadium seating bowl with cellular antenna masts mounted on lighting rig — Photo by the blowup on Unsplash")

## When Radio Signals Learn to See

The core premise of ISAC—often codified in academic literature as Joint Communication and Sensing (JCAS)—is straightforward in theory, yet punishingly complex in practice.

Traditional mobile networks discard signal reflections as channel interference or multipath distortion. ISAC, by contrast, treats those reflections as rich environmental telemetry. By leveraging orthogonal frequency-division multiplexing (OFDM) waveforms already deployed in commercial networks, an ISAC-enabled base station can decode incoming subscriber uplink traffic while simultaneously processing the faint, delayed echoes bouncing off physical structures, moving vehicles, and human bodies.

According to technical specifications mapped out by the [3GPP](https://www.3gpp.org) in Releases 19 and 20, sensing operations must coexist with user data without cannibalizing mission-critical network throughput. In the Samsung-Verizon demonstration, engineers utilized dynamic beamforming across millimeter-wave (mmWave) and upper mid-band frequencies to illuminate specific geographical sectors.

By calculating the precise time delay, Doppler shift, and angle-of-arrival of backscattered cellular signals, the network generated a real-time, high-definition kinetic spatial map of the arena’s access plazas. The system detected micro-movements across dense crowds and tracked fast-moving autonomous drones in three dimensions, all while supporting concurrent multi-gigabit streaming for spectators in the stands.

As mobile operators explore new monetization avenues for enterprise connectivity in our evolving [5g](/5g/) ecosystem, the ability to sell "sensing-as-a-service" to venue operators, transit authorities, and municipal agencies fundamentally transforms the economics of site deployment.

## The vRAN Advantage: Radar as a Pure Software Service

What makes this specific trial a milestone is not merely that ISAC worked; it is where the processing took place.

Previous industrial demonstrations of cellular sensing relied on bespoke, purpose-built hardware: dedicated radar signal processors hardwired directly into proprietary baseband units. Samsung and Verizon executed this trial over Verizon’s commercial vRAN architecture, utilizing Samsung’s fully virtualized distributed unit (vDU) and centralized unit (vCU) software hosted on commercial off-the-shelf (COTS) x86 server infrastructure.

By treating sensing as a containerized software workload rather than an ASIC-bound hardware function, the operators accomplished several key breakthroughs:

*   **Dynamic Resource Allocation:** When spectator traffic peaked during halftime, the virtualized network automatically allocated more compute cycles and time-frequency resource blocks (RBs) to user payload data. When data demands dropped, compute headroom dynamically shifted to high-resolution sensing tasks.
*   **Zero Additional Field Hardware:** The sensing capabilities were integrated as software modules on top of Samsung’s existing massive MIMO radios. No auxiliary radio heads or specialized field upgrades were required.
*   **Direct Core Integration:** The environmental data generated by the radio reflections was routed directly through standard API frameworks, allowing venue security dashboards to consume radar point-clouds without intermediating translation boxes.

Running radar algorithms alongside baseband stacks requires blistering compute throughput and near-zero jitter. The trial proved that contemporary commercial servers, boosted by modern algorithmic acceleration, can manage the heavy matrix mathematics of synthetic aperture radar (SAR) channel estimation without destabilizing the latency budgets required for standard voice and data traffic.

## Comparing Sensing Paradigms: Why ISAC Changes the Field

Venue security, urban traffic management, and industrial logistics have long relied on a fragmented patch of optical, acoustic, and radio technologies. ISAC introduces a unified paradigm that avoids many of the mechanical and operational bottlenecks inherent to dedicated hardware arrays.

| Metric / Capability | Traditional Mechanical Radar | Optical Cameras & Computer Vision | Dedicated LiDAR Units | 5G-Advanced / 6G ISAC |
| :--- | :--- | :--- | :--- | :--- |
| **Hardware Footprint** | Dedicated, heavy rotating or phased arrays | Distributed camera clusters | Expensive optical transceivers | Zero extra footprint (uses existing cell radios) |
| **All-Weather Resilience** | High | Low (degrades in heavy rain, smoke, glare) | Medium (vulnerable to dense fog, rain) | Extremely High (unaffected by lighting or precipitation) |
| **Privacy Compliance** | High (point-cloud telemetry) | Low (captures PII / facial data) | High (point-cloud telemetry) | High (RF reflections, zero visual identification) |
| **Velocity Tracking** | Direct (Doppler shift) | Indirect (frame-by-frame inference) | Indirect (frame-by-frame inference) | Direct (Doppler shift across OFDM subcarriers) |
| **Capital Deployment Cost** | Very High | Medium | Very High | Low (software-defined upgrade on vRAN) |

As shown above, the technical advantages of ISAC do not necessarily stem from beating the millimeter-level spatial fidelity of high-end optical systems, but from delivering dependable, privacy-preserving kinetic tracking at scale through infrastructure that has already been deployed and paid for.

![enterprise data center server racks glowing with network cabling in high tech facility](https://images.unsplash.com/photo-1762163516269-3c143e04175c?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxlbnRlcnByaXNlJTIwZGF0YSUyMGNlbnRlciUyMHNlcnZlciUyMHJhY2tzJTIwZ2xvd2luZyUyMHdpdGglMjBuZXR3b3JrJTIwY2FibGluZyUyMGluJTIwaGlnaCUyMHRlY2glMjBmYWNpbGl0eXxlbnwwfDB8fHwxNzg5ODExODQ2fDA&ixlib=rb-4.1.0 "enterprise data center server racks glowing with network cabling in high tech facility — Photo by Domaintechnik on Unsplash")

## The Killer Applications Unlocked in the Arena

During the sports event demonstration, the consortium put the hybrid network through four distinct operational stress tests designed to simulate smart-city conditions:

### 1. Dynamic Crowd Density and Bottleneck Mitigation
Rather than relying on optical video streams that can trigger legal scrutiny over facial recognition, the ISAC system calculated physical crowd density at critical bottleneck areas outside the stadium turnstiles. The network measured aggregate Doppler reflections to detect stall patterns and stampede precursors, automatically alerting operations staff to divert foot traffic minutes before physical congestion escalated.

### 2. Low-Altitude Drone Detection
Unauthorized consumer drones represent an escalating headache for live stadium events. Traditional civilian air surveillance often struggles with low-altitude, small-radar-cross-section quadcopters obscured by stadium architecture. By utilizing low-elevation, wide-aperture 5G MIMO beams, the Samsung-Verizon setup successfully tracked a commercial drone flying below light-pole level, charting its trajectory and altitude in real time.

### 3. Non-Line-of-Sight Perimeter Security
Because RF signals can propagate around physical obstacles via diffraction and controlled multi-bounce scattering, the sensing system managed to flag intrusions behind structural partitions where security cameras suffered blind spots. For critical infrastructure providers exploring [future tech](/future-tech/) architectures, this capability turns standard cellular coverage into a persistent, non-line-of-sight electronic tripwire.

### 4. Centimeter-Grade Asset Tracking Without GPS Tags
High-value broadcast and medical assets moving through covered indoor tunnels—where Global Positioning System signals cannot penetrate—were tracked passively. The backscatter signatures of service vehicles provided velocity and directional tracking without requiring active battery-powered RFID tags or expensive ultrawideband (UWB) beacons.

## The Looming Privacy Debate and the Road to 6G

While the operational efficiency of ISAC is indisputable, turning standard communications networks into ubiquitous radar sensors introduces a profound regulatory and ethical challenge.

Historically, individuals could opt out of network tracking by simply switching their smartphones to airplane mode or leaving them at home. With ISAC, the network tracks physical presence, movement velocity, and spatial orientation via physical RF reflection off the human body itself. You do not need a connected device in your pocket for an ISAC-enabled base station to register your movement through a city street or arena concourse.

This shift will inevitably demand aggressive scrutiny from privacy regulators. Because the generated point clouds contain no facial features, proponents argue that ISAC is fundamentally more privacy-centric than optical surveillance. However, gait analysis algorithms—which can identify individuals based purely on the cadence of their movement—are advancing rapidly, raising valid questions around biometric consent and [data security](/data-security/) governance.

Engineers will need to design robust algorithmic boundaries to ensure that commercial telecommunications infrastructure cannot be repurposed for covert kinetic tracking without rigorous oversight. Organizations like the [IEEE](https://www.ieee.org) are already actively working on standardized ethical frameworks and sensing resolution caps within emerging communication drafts.

## The Foundation for the Next Decade of Networks

The Samsung-Verizon trial at this global event demonstrates that the telecom industry's long-standing vision of "spatial intelligence" is moving out of university simulations and into carrier-grade deployment.

By grounding the implementation in software-defined vRAN, Verizon has decoupled sensing capabilities from proprietary silicon cycles. As new AI-based channel estimation models emerge, operators will be able to push over-the-air firmware updates to their base stations, turning yesterday's 5G data mast into tomorrow's micro-climate monitor, traffic conductor, or automated factory controller.

We are watching the fundamental definition of a network expand. The cellular grid is no longer just a digital transport layer; it is becoming an active, tactile nervous system for the physical world.
