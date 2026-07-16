# STRAFTAT Melee Reach Overlay

Source and packaging project for a vanilla-compatible Katana reach visualization.

## What the game actually does

Analysis of the supplied `Assembly-CSharp.dll` showed that `MeleeWeapon` has no single range value. It owns:

- `collisionObj : GameObject`
- `collisionScript : MeleeChildCollision`

`MeleeWeapon.TriggerAttack()` opens `collisionScript.canHit` and `canHitEnvi`. Damage is then driven by `MeleeChildCollision.OnCollisionEnter(...)`. The mod therefore visualizes the animated collision object rather than guessing a radius.

## Build requirements

- .NET SDK capable of targeting .NET Framework 4.7.2
- STRAFTAT installed with BepInEx 5
- The game assemblies from `STRAFTAT_Data/Managed`

Run:

```powershell
.\tools\Build.ps1 -GamePath "C:\Program Files (x86)\Steam\steamapps\common\STRAFTAT"
```

The script copies build-only references into `lib`, builds the project, and places the DLL in `thunderstore/plugins`. Do not commit or redistribute the copied game assemblies.

## Project status

Version 0.2.0 is statically compiled against the assembly set collected on 2026-07-16. It still requires in-game verification because the game cannot be run in the build environment.
