# How to Watch SpaceX Catch Super Heavy: Flight Telemetry and Guide

> SpaceX is broadcasting its next Super Heavy booster catch attempt at Starbase. Here are the crucial flight milestones and telemetry cues to track live.

By InnotechInsider Staff · SpaceX & Space · Nov 17, 2026
Canonical URL: https://innotechinsider.com/spacex/spacex-super-heavy-catch-attempt-livestream-guide/

> **TL;DR** Catching a 230-foot Super Heavy booster with mechanical tower arms demands pinpoint real-time margins; here is how to read the livestream telemetry and tell a successful recovery from an abort.

Few sights in aerospace engineering rival the sheer kinetic audacity of catching a returning rocket stage midair. Watching SpaceX maneuver a 33-engine Super Heavy booster out of supersonic descent and slip it into the mechanical arms of the launch tower—affectionately nicknamed "Mechazilla"—remains one of the most intense live webcasts in modern spaceflight.

For casual viewers, the broadcast can look like a blur of engine plumes, thermal distortion, and sudden camera cuts. But the stream displays dense diagnostic data if you know where to look. Understanding the guidance thresholds, burn sequences, and abort gates lets you evaluate the flight profile in real time rather than waiting for the hosts to explain what just happened.

## The Choreography of the Chopsticks

The recovery process bypasses conventional landing gear entirely. Adding robust landing legs to a vehicle the scale of Super Heavy penalizes payload mass directly to orbit, which clashes with the broader economics of [spacex](/spacex/) infrastructure. Instead, the ground infrastructure absorbs the structural stress.

![SpaceX Starbase launch tower chopsticks mechanical arms](https://images.unsplash.com/photo-1634175734730-feeb73322946?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxTcGFjZVglMjBTdGFyYmFzZSUyMGxhdW5jaCUyMHRvd2VyJTIwY2hvcHN0aWNrcyUyMG1lY2hhbmljYWwlMjBhcm1zfGVufDB8MHx8fDE3OTQ5MzQwMDZ8MA&ixlib=rb-4.1.0 "SpaceX Starbase launch tower chopsticks mechanical arms — Photo by Anirudh on Unsplash")

The catch mechanism relies on two massive steel catching arms, commonly referred to as chopsticks, attached to the orbital launch mount's tower carriage. During the catch sequence, these arms extend outwards over the pad surface.

The rocket does not rest on the floor of the arms. Instead, the booster carries hardened structural catch pins—load points positioned near the grid fin assemblies at the forward section of the tank. As the vehicle approaches zero velocity relative to the ground, the booster maneuvers directly between the open arms. The ground system tracks the booster's descent rate, adjusting the hydraulic rails to clamp beneath the pins and absorb the remaining vertical energy.

Catching the stage requires millisecond-level reaction times. If the booster's velocity vector or lateral position drifts outside strict performance bands, the flight computer must instantly choose an alternate trajectory.

## Critical Milestones to Monitor on the Feed

When watching the public webcast on X (formerly Twitter) or dedicated tracking platforms, the telemetry graphic at the bottom of the screen provides the real story. Keep an eye out for these sequential phases:

| Flight Milestone | Typical Mission Time | Key Visual or Telemetry Cue | Operational Goal |
|---|---|---|---|
| Liftoff | T-00:00:00 | All 33 Raptor engines ignite | Clear launch mount cleanly |
| Hot Staging | ~T+00:02:45 | Ring separation visible, Ship ignites | Staging without coast down |
| Boostback Burn | ~T+00:03:00 | Center engine cluster re-ignites | Reverse booster horizontal momentum |
| Grid Fin Guidance | ~T+00:04:30 | Fins visibly rotate during descent | Aerodynamic steering in thin air |
| Landing Burn Commit | ~T+00:06:30 | 13-engine ignition down to 3 | Rapid deceleration toward tower |
| Mechazilla Capture | ~T+00:06:55 | Booster hovers between arms | Contact pins engage rail pads |

The boostback burn is the first indicator of whether a tower catch is even on the table. During this window, the flight software computes internal health metrics across propellant reserves, hydraulics, and avionics. According to public regulatory filings tracked by the [Federal Aviation Administration commercial space licensing](https://www.faa.gov/space) office, launch authorizations strictly govern the trajectory corridors permitted for terrestrial returns versus ocean splashdowns.

![Super Heavy rocket booster landing burn engines](https://images.unsplash.com/photo-1517976487492-5750f3195933?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxTdXBlciUyMEhlYXZ5JTIwcm9ja2V0JTIwYm9vc3RlciUyMGxhbmRpbmclMjBidXJuJTIwZW5naW5lc3xlbnwwfDB8fHwxNzk0OTM0MDA3fDA&ixlib=rb-4.1.0 "Super Heavy rocket booster landing burn engines — Photo by SpaceX on Unsplash")

## The Abort Gate: Divert vs. Catch

A catch attempt is never guaranteed, even if the launch looks nominal on ascent. SpaceX uses automated "go/no-go" gates governed by flight software on both the rocket and the ground side. Neither mission control nor the vehicle will attempt a catch if any primary system reports an anomaly.

1. **System Health Check (High Altitude):** Prior to atmospheric entry, the vehicle evaluates tank pressurization, steering authority on the titanium grid fins, and engine restart readiness. If any metric falls outside bounds, the booster targets an offshore corridor in the Gulf of Mexico.
2. **Trajectory Biasing:** The booster does not aim straight at the launch tower during its supersonic fall. It maintains an offset trajectory pointing into the open water until the landing burn begins.
3. **The Divert Decision:** If the final burn fails to ignite the planned number of inner Raptor engines, or if navigation sensors detect high winds near the tower carriage, the vehicle does not correct toward the pad. It simply continues its offset vector and impacts the water safely offshore.
4. **Tower Readiness Check:** Simultaneously, the ground system at Starbase runs automated health routines on the hydraulic carriage winch, dampeners, and optical tracking cameras. If ground computers encounter a communication lapse, the booster receives an abort wave-off command.

Watching telemetry numbers during the landing burn reveals whether the vehicle is banking toward the tower (a catch attempt) or holding a vertical burn away from the shore (an ocean dump). The development path documented in the [Starship development history](https://en.wikipedia.org/wiki/SpaceX_Starship) highlights that early iterations prioritized safe water disposal whenever telemetry fell outside narrow target envelopes.

## The Role of Autonomous Telemetry

The guidance loops coordinating the final ten seconds rely on localized radar, LiDAR, and high-frequency optical arrays mounted directly to the launch structure. GPS signals alone are far too coarse to settle a multimillion-pound steel cylinder onto mechanical rails within inches of clearance.

These high-speed sensing loops mirror the edge processing innovations expanding throughout [future tech](/future-tech/) disciplines, where microsecond mechanical adjustments must occur without human latency. By the time the webcast commentators call out the terminal dive, the booster has executed millions of calculations regarding thrust vectoring, throttle modulation, and center-of-mass shifts as the propellant tanks drain.

Watching the stream closely, you will see the three central Raptors gimballing aggressively. The engines must kill vertical velocity while balancing the aerodynamic forces buffeting the tall fuselage.

## Why This Matters for Lunar Logistics

While catching the booster offers undeniable livestream drama, the operational motivation is purely industrial. Conventional sea recoveries require recovery ships, crane operations, port transits, and lengthy inspections—a process that often takes days or weeks before a core returns to a hangar.

Catching the vehicle at the pad eliminates the transit link. The long-term vision requires placing the booster back onto the launch mount within hours to stage another launch. That flight rate is vital for the propellant depot flights needed to support deep-space missions, including the [NASA Artemis program](https://www.nasa.gov/specials/artemis/) which relies on a specialized Starship variant to deliver astronauts to the lunar surface.

Mastering this capture sequence transforms the launch pad into an active capture system. When you tune into the next attempt, look past the engine fire and focus on the data displays: the descent velocity, the burn ignite markers, and the micro-adjustments of the chopstick carriage. Those numbers show whether industrial orbital transport is taking another step toward routine operations.
