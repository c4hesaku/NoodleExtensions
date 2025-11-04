# Noodle Extensions

A port of the Noodle Extensions mod made originally for the PC version of Beat Saber to the Oculus Quest platform.

## 1.40.8 To-Do

<h3><u>This list is not final and will continue to grow</u></h3>

- [x] Fix note jump animation (notes simply pop into existence rather than flying into view)
- [ ] Fix notes being invisible on pretty much all modcharts. Perhaps notes that are on a track?
- [ ] Fix audio being drowned out for seemingly no reason. Common in Doppelganger. Perhps an issue with walls?
- [ ] Fix no badcut
- [ ] Fix notes looking towards (0, 0, 0). Maybe calculated in `src/hooks/NoteJump.cpp`
- [ ] Fix crash when restarting a modchart
- [ ] Fix crash when Replay tries to load a modchart replay
- [x] Investigate jump distance / speed
- [ ] Investigate frame rate / stutter issues
- [ ] Search for Chroma issues

## Bonus 1.40.8 fixes / features

These would be nice to fix and implement, but were already broken / missing in 1.37 and therefore aren't required if I'm simply going for 1.37 parity.

- [ ] Iirc saber animation was broken


## FAQ (Frequently Asked Questions)
- Why are the wall colors not the same as PC (desaturated, transparent etc.)?
  - Due to the Quest not having distortion on walls, Noodle Extensions will attempt to change the walls materials to solid if these conditions are met:
    - Wall color alpha (controlled by Chroma) is greater than or equal 0
    - Dissolve animation is being applied
- Bombs are not coloring/are always black
  - A bug specific to Quest causes bombs to lose their color/default to black when dissolve animation is being applied. It is not certain if this bug will be fixed or worked around.
- Why does Noodle Extensions disable my Qosmetics notes/walls?
  - Qosmetics notes/walls drastically reduce performance especially in Noodle maps and also ruin the artistic experience. 
- Why do you suggest disabling Mapping Extensions? It works fine for me
  - While it _could_ work, we didn't extensively test the impact of performance or stability using Mapping Extensions. It's at your discretion if you choose to use Mapping Extensions simultaneously with Noodle.
  - While some maps do "require" both Noodle Extensions and Mapping Extensions, this is not a supported scenario in either PC or Quest and should be discouraged.
- Where are Tracks/CustomJSONData QMod downloads?
  - Noodle Extensions and Chroma will download these dependencies automatically
- Noodle Extensions isn't loading/working and PinkCore says I don't have the mod installed
  - Try to reinstall Noodle Extensions and update Chroma to at least version 2.5.7 or newer.
- I found a map that doesn't work!!!!11!!11!/Noodle is missing a feature
  - You most likely downloaded the wrong map as most Noodle features are supported (no exceptions except the TODO)
  - In the case you are absolutely certain you found a bug/missing feature, report it in GitHub issues along with a log and steps to reproduce the issue. Footage of said map is also recommended being provided.

## Building from Source

You'll need [qpm_rust](https://github.com/RedBrumbler/QuestPackageManager-Rust), Powershell, Ninja, and CMake in `PATH`.

You'll also need the latest Android NDK. Create a file called `ndkpath.txt` containing the path to the directly where you extracted the ndk to.

```sh
qpm-rust restore
qpm-rust cache legacy-fix
pwsh ./build.ps1
pwsh ./createqmod.ps1 noodle_extensions
```

## What still needs to be done?
- Left handed mode
- Beatmap note/obstacle/bomb count (includes fakes)
- Some maps such as Centipede by totally balloon have fake notes registered as real notes
- Make Noodle only run on Noodle maps
