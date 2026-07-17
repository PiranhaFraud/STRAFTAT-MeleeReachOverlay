# STRAFTAT Throwable Visuals

Vanilla-compatible BepInEx overlay for STRAFTAT that visualizes the currently held throwable/projectile launcher's deterministic flight path.

## Test-1 scope

- Reads STRAFTAT's existing `DualLauncher.trickShot.prediction` path when available.
- Draws multi-segment arcs and bounce markers.
- Marks the final predicted impact/end point.
- Reads `explosionRadius` from the runtime projectile prefab and draws a wireframe blast sphere.
- Attempts to place cooked-grenade blast visualization at the fuse-expiry position when path timing is exposed.
- Uses a reflective ballistic fallback for launcher prefabs without TrickShot prediction.
- Does not alter projectiles, damage, physics, networking, ammo or player movement.

## Controls

- `F11`: toggle overlay
- `F12`: diagnostics to `BepInEx/LogOutput.log`

All settings are exposed through BepInEx config and should appear in STRAFTAT Mod Menu.

## Runtime basis

STRAFTAT's `DualLauncher` copies `HeathenEngineering.PhysKit.TrickShot.prediction` into the projectile's networked ballistic path. The overlay reads and draws that same local prediction instead of estimating a generic parabola whenever it is available.
