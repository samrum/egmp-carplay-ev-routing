# 0.4.3 (samrum fork) — experimental

- Signed with samrum's mod key (author uuid 6e3acbe6-b49b-8948-b938-4e822bf3706d) instead of Isaac Wisdom's. HMG-API won't install official releases over this build, or this build over an official one, without uninstalling first.
- Ioniq 5 consumption values from the Leafia trip tuning (US Ioniq 5, 2026-11-08/09 drives): reference values x0.6 for the town and mid-speed slots, x0.9 for the three highway slots (8-10, 75 mph). Capacity stays 77.4 kWh (pinned in `VehicleSource`). EV6 profile unchanged.
- Build notes for Linux: JDK 17 (`--release 7` needs a JDK before 20), a `--java-home` whose `include/` also holds `linux/jni_md.h`, and an android.jar without `org/json` (Robolectric android-all 4.4 with `org/json/*` removed works).

# 0.4.3 — experimental

- Send vehicle status every ten seconds instead of every five seconds.
- Average valid auxiliary-power samples over one-minute windows, round the result to the nearest 25 W and publish it only at minute boundaries. Hold the profile default until the first complete window and retain the last published average through missing samples.
- Add deterministic regression coverage for window timing, rounding and missing samples.

# 0.4.2 — experimental

- Floor live battery state of charge to a whole percent before sending it to Apple Maps, matching Hyundai's EV app treatment of the half-percent `DISPLAY_SOC` signal.
- Add regression coverage for half-percent SOC values and invalid inputs.
- Native patch, energy models, auxiliary-power behavior and five-second update policy are unchanged.

# 0.4.1 — experimental

- Accept the 2022 US Ioniq 5 (`NEEV.USA`, firmware `260507`) with the existing 77.4 kWh profile; on-car validation pending.
- Include both detected native-library MD5 hashes in rejection logs; exact-hash guards remain unchanged.
- Native patch, energy models and five-second update policy are unchanged.

# 0.4.0 — experimental first release

- One signed native HMG-API mod download with automatic profile selection at Apply, requiring official beta6 or newer.
- Live SOC/range/auxiliary power and bundled vehicle contracts.
- Exact native-hash gates, HMG-API map checks, signed updates, and rotating logs. Optional NEMESIS wrappers remain available for testing.
- Ioniq 5 integration tested; EV6 profile copied and unvalidated.
- Known issue: route recalculation at the five-second status cadence remains under investigation.
