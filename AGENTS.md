# Repository Guidelines

## Project Structure & Module Organization
This repository is a small Godot 4.5.1 Mono mod with one main C# source file at `RouteSuggest.cs`. Project metadata lives in `project.godot`, `RouteSuggest.csproj`, `RouteSuggest.json`, and `mod_manifest.json`. Packaging scripts are in `build.sh` and `install.sh`. Example user config is `RouteSuggestConfig.json.example`. Visual assets are kept at the root (`icon.svg`, `screenshot.png`) and in `RouteSuggest/` (`mod_image.png`). Build output is generated into `dist/` and should not be committed unless a release process explicitly requires it.

## Build, Test, and Development Commands
Use the documented source workflow from the repo root:

```bash
./build.sh
./install.sh
```

`./build.sh` copies `sts2.dll`, builds the Godot/.NET solution, exports `RouteSuggest.pck`, and creates a versioned zip. `./install.sh` copies `dist/*` into the local Slay the Spire 2 `mods/RouteSuggest` folder on Linux or macOS. Prerequisites are .NET 9, Godot 4.5.1 Mono, `jq`, `zip`, and a local game install. The scripts do not currently handle Windows builds.

## Coding Style & Naming Conventions
Follow the existing C# style in `RouteSuggest.cs`: 4-space indentation, file-scoped namespace, PascalCase for types/methods/properties, camelCase for locals and parameters. Keep XML doc comments on public types and behavior-heavy methods. Preserve the current JSON naming style: config keys use `snake_case` in files such as `RouteSuggestConfig.json.example`, while C# members remain PascalCase.

## Testing Guidelines
There is no automated test suite in this repository today. Validate changes by rebuilding the mod and checking behavior in game: path highlighting, overlap priority, config loading, and any schema migration or default-config fallback. If you change config fields or versioning, update `RouteSuggestConfig.json.example`, `README.md`, and release metadata together.

## Commit & Pull Request Guidelines
Recent history uses short, imperative commit subjects such as `Add expert scoring mode with adjacency bonuses` and `Bump supported game versions`. Keep subjects concise and descriptive. Pull requests should explain gameplay impact, list the game/mod versions tested, and include screenshots when map rendering or UI-visible behavior changes. Link the related issue when available.
