# Lockheed and Verizon Turn Cellular 5G Towers Into Drone Radar

> Lockheed Martin and Verizon are turning commercial 5G infrastructure into bistatic radar networks, tracking rogue drones using ambient cellular radio reflections.

By InnotechInsider Staff · 5G & Connectivity · Aug 16, 2026
Canonical URL: https://innotechinsider.com/5g/lockheed-verizon-5g-drone-radar-detection/

> **TL;DR** Telecom infrastructure is quietly evolving into a national defense sensor web as Lockheed Martin and Verizon demonstrate how commercial 5G towers can track rogue drones without mounting a single new radar dish.

Every cubic meter of urban airspace is bathed in an invisible, churning soup of electromagnetic radiation. Thousands of 5G cell towers constantly negotiate connections with smartphones, cars, and industrial IoT nodes, firing directed beams of radio frequency (RF) energy back and forth across city skylines.

To a mobile carrier, those signals are billable gigabytes. To a defense contractor, they are an unexploited, multi-gigahertz radar illuminator.

In an ambitious technological convergence, Lockheed Martin and Verizon have demonstrated a method to convert off-the-shelf, commercial 5G cellular networks into wide-area drone detection arrays. By capturing the microscopic reflections and scattering patterns created when an airborne object cuts through ambient cellular transmissions, the system creates a high-fidelity airspace tracking grid—without deploying dedicated military radar hardware or firing active sensor pings that give away the tracker's position.

The implications reach far beyond military perimeter security. As low-altitude drone incursions plague commercial airports, power plants, and sporting venues, the project marks the beginning of dual-use telecommunications: a world where the infrastructure that powers mobile video streaming also acts as an omnipresent, sovereign surveillance umbrella.

![military drone flying over urban cityscape during twilight](https://images.unsplash.com/photo-1759683832173-ad2a151a192c?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxtaWxpdGFyeSUyMGRyb25lJTIwZmx5aW5nJTIwb3ZlciUyMHVyYmFuJTIwY2l0eXNjYXBlJTIwZHVyaW5nJTIwdHdpbGlnaHR8ZW58MHwwfHx8MTc4Njg2MTM5NXww&ixlib=rb-4.1.0 "military drone flying over urban cityscape during twilight — Photo by Miguel A Amutio on Unsplash")

---

## The Physics of Parasitic Radar

Traditional air-defense radar systems are active: a transmitter emits a high-power radio pulse and waits for the echo to bounce back to a collocated receiver. While effective over long distances, active radar suffers from catastrophic blind spots in dense urban environments. Buildings create severe ground clutter, and low-flying consumer quadcopters—often constructed from lightweight carbon fiber and plastic—present microscopic radar cross-sections (RCS) that disappear against the physical noise of the city.

Furthermore, active military radar transmitters are expensive, energy-hungry, and function like flare guns on an electromagnetic battlefield, advertising their exact location to anyone with basic signal-intercept equipment.

The Lockheed-Verizon approach relies on a principle known as [passive bistatic radar](https://en.wikipedia.org/wiki/Passive_radar). Instead of generating new signals, the system treats existing commercial base stations as "illuminators of opportunity."

When a drone enters the RF corridor between a 5G gNodeB base station and nearby user equipment, it disrupts the signal. The drone's airframe and spinning rotor blades induce subtle phase variations, time delays, and Doppler shifts in the carrier wave.

By placing specialized, synchronized passive receiver modules around the network perimeter, Lockheed’s signal-processing algorithms can cross-reference the direct signal from the tower against the scattered signal bouncing off the intruder. By calculating the Time Difference of Arrival (TDOA) across multiple towers, the software computes the drone’s precise three-dimensional coordinate, vector, and altitude in real time.

---

## Moving Beyond Hardware: Software-Defined Airspace

The core breakthrough does not require Verizon to rip and replace its physical antenna masts. Instead, it rides on the architectural evolution of modern cellular networks.

With the rollout of 5G Standalone (5G SA) architectures and Open Radio Access Networks (Open RAN), telecom networks are increasingly software-defined. Functions that once required dedicated silicon inside proprietary chassis now execute as virtualized network functions (VNFs) in edge data centers.

By analyzing the continuous channel state information (CSI) already collected by base stations for beamforming optimization, the software extracts kinetic intelligence from the data stream. In areas where low latency and continuous situational awareness intersect, deploying distributed sensor software at the edge allows teams focused on [5g](/5g) infrastructure to deliver actionable situational telemetry straight into military command-and-control frameworks.

### The Micro-Doppler Fingerprint

Detecting a moving object is only half the battle; identifying what that object is presents an equal challenge. A flock of pigeons, an errant plastic bag, and a loitering munitions drone look remarkably similar to a crude RF detector.

To solve this, Lockheed Martin applies machine learning models to the received signals to isolate "micro-Doppler" signatures. As drone propellers rotate at thousands of revolutions per minute, they create distinct harmonic modulation patterns within the scattered 5G wavefront.

Because a dual-rotor hobby drone modulates RF differently than an octocopter carrying an explosive payload or a fixed-wing surveillance drone, the system can instantly classify the platform type, payload capacity, and flight dynamics before human operators even acquire visual contact.

---

## Comparing Low-Altitude Air Defense Architectures

To understand why defense strategists are pursuing ambient RF sensing over traditional approaches, consider how current low-altitude Counter-Unmanned Aircraft Systems (C-UAS) stack up across cost, stealth, and operational complexity.

| System Capability | Dedicated Active Radar | Optical / Infrared Cameras | Dedicated Acoustic Arrays | 5G Ambient RF Sensing |
| :--- | :--- | :--- | :--- | :--- |
| **Capital Expenditure** | Extremely High ($500k+ per node) | Moderate to High | Low to Moderate | Low (Uses Existing Towers) |
| **RF Stealth Profile** | None (Actively Emits RF) | Passive (Zero Emissions) | Passive (Zero Emissions) | Passive (Zero Emissions) |
| **Urban Clutter Tolerance**| Poor (Multipath Echoes) | Poor (Line-of-Sight Blocked)| Very Poor (High Ambient Noise) | High (Multi-Angle Geometry) |
| **Weather Resilience** | High | Low (Degraded by Fog/Rain) | Low (Degraded by Wind) | High |
| **Scalability** | Limited by Cost & Spectrum | Limited by Line-of-Sight | Limited by Sensor Range | Massive (Covers Telecom Footprint)|

---

## The Dual-Use Playbook: From Base Defense to Smart Cities

The partnership aligns closely with the United States Department of Defense's modernization priorities, specifically its focus on commercial 5G experimentation across military bases. As asymmetric drone warfare transforms modern conflicts, military installations inside domestic borders face unprecedented surveillance and kinetic threats from cheap, autonomous systems.

Securing a sprawling domestic base like Fort Moore or Norfolk Naval Station with traditional radar rings is prohibitively expensive and legally complicated due to domestic spectrum allocations managed by the [Federal Communications Commission](https://www.fcc.gov). Tapping into the commercial 5G networks that already cover these facilities solves the deployment bottleneck overnight.

![modern telecommunications tower against sky at sunset](https://images.unsplash.com/photo-1581167408225-a6fe072be70c?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxtb2Rlcm4lMjB0ZWxlY29tbXVuaWNhdGlvbnMlMjB0b3dlciUyMGFnYWluc3QlMjBza3klMjBhdCUyMHN1bnNldHxlbnwwfDB8fHwxNzg2ODYxMzk1fDA&ixlib=rb-4.1.0 "modern telecommunications tower against sky at sunset — Photo by Vivek Doshi on Unsplash")

Yet the civilian applications are just as expansive. The Federal Aviation Administration (FAA) and international regulators are currently laying the groundwork for Unmanned Aircraft System Traffic Management (UTM) to enable commercial drone deliveries and urban air mobility (air taxis). Building an entirely new nationwide radar system to manage low-altitude traffic would cost tens of billions of dollars. Integrating RF sensing capabilities into carrier networks offers a pre-built foundation for commercial airspace management.

In enterprise contexts, facilities from semiconductor fabrication plants to data centers are increasingly targeted by industrial espionage teams using micro-drones. Incorporating RF-based drone monitoring directly into corporate security architectures gives facilities managers a real-time perimeter alert mechanism, bridging the gap between physical perimeter safety and modern [cybersecurity](/cybersecurity) protocols.

---

## The Regulatory and Privacy Minefield

Despite its operational brilliance, transforming civilian telecommunications infrastructure into a passive surveillance mesh introduces complex technical, legal, and civil liberty challenges.

First is the issue of resolution and coverage. 5G networks operate across multiple spectrum tiers. Millimeter-wave (mmWave) frequencies provide pinpoint positional accuracy down to centimeters due to their vast bandwidth, but their signals degrade rapidly over distance and cannot penetrate heavy foliage or rain. Mid-band (sub-6 GHz) spectrum travels much farther and forms the backbone of nationwide 5G coverage, but it yields lower spatial resolution, making the detection of micro-drones significantly more reliant on complex predictive AI filtering.

RF SENSING SPECTRUM TRADEOFF:
- mmWave (24-40 GHz) → High Accuracy / Short Range / High Attenuation
- Mid-Band (1-6 GHz) → Medium Accuracy / Wide Coverage / Deep Penetration
- Low-Band (\<1 GHz) → Low Spatial Resolution / Wide Footprint

Then comes the privacy dilemma. If a commercial cellular network can be tuned to detect a two-pound plastic drone hovering near an electrical substation, it can theoretically track other physical movements in public spaces:
* Monitoring vehicular traffic dynamics with sub-lane precision.
* Mapping pedestrian density and crowd movement patterns without phone telemetry.
* Tracking physical assets through ambient radio shadows.

While telecommunications providers maintain that the underlying data streams process environmental channel distortions rather than consumer payload data, civil liberties groups are likely to scrutinize any technology that blurs the line between public communications utilities and military-grade spatial monitoring. As governments grapple with policies around [future tech](/future-tech) governance, defining the legal boundary between "optimizing network performance" and "conducting ambient spatial surveillance" will become a central regulatory battleground.

---

## The Sentry in the Skyline

The collaboration between Lockheed Martin and Verizon is a preview of a broader industrial trend: the convergence of communications, sensing, and edge computing. In standard telecommunication industry roadmaps, this paradigm is codified as Integrated Sensing and Communications (ISAC), a core pillar of upcoming [3GPP 5G-Advanced](https://www.3gpp.org) and future 6G specifications.

Historically, humans built networks to move bits from point A to point B. In the decade ahead, those same networks will continuously map the physical reality of the spaces they occupy.

By harvesting the ghost echoes of the digital age, defense contractors and mobile operators are demonstrating that the tools needed to secure tomorrow’s airspace may not require new weapons or dedicated sensors. They were already bolted to the cell towers above our heads, waiting for the right software to wake them up.
