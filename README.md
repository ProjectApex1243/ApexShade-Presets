# ApexShade presets

Every `.ini` in [`presets/`](presets) shows up on the in-game **SHADERS** tab (marked *online*) the next time players
launch the game. No app update needed. Delete a file here and it disappears from the game too.

## Adding a preset

1. Get a ReShade preset `.ini`: one from ReShade itself, or export one from Unity
   (profile inspector → *Export as ReShade Preset (.ini) for GitHub*, or *Apex > ApexShade > Export Presets as .ini*).
2. Put it in `presets/`. The file name is the name players see (`Gloomy.ini` → GLOOMY).
3. Commit and push. That's it.

A preset with the same name as one built into the game replaces it, so built-in presets can be tweaked from here too.

## What works

- Only the effects built into the game can be used: see [`techniques.txt`](techniques.txt) (SweetFX, prod80, Deband).
  Techniques from other shader packs are skipped. If nothing in a preset can run, the whole preset is skipped.
- Only the techniques in the `Techniques=` line are used, in `TechniqueSorting=` order. Slider values come from the
  `[File.fx]` sections; anything not listed keeps the effect's default.
- Values are clamped to each slider's range. Preprocessor definitions are ignored.
- Limits: 64 presets, 256 KB per file, 8 passes per preset (each pass costs frame time on Quest; 1-3 is comfortable).

This repo has to stay **public**: the game reads it without logging in. Players get updates once per launch, and the
last copy keeps working offline.
