# groot-plugins

Plugin registry for the [Groot](https://github.com/JohnEsleyer/groot) game engine.

## Overview

This repo contains `index.ron` — a registry of available Groot plugins. The `groot plugin list` CLI command reads from this file to display available plugins.

## Registry Format

```ron
(
    version: "1.0",
    plugins: [
        (
            name: "audio",
            description: "Simple audio synthesizer & sound effects for Groot",
            author: "John Esleyer",
            path: "../groot-plugin-audio",
            repo: "https://github.com/JohnEsleyer/groot-plugin-audio",
        ),
        // ... ztarget, kinematics, combat, skeletal, navmesh, gamestate, dialogue, audio-interactive
        (
            name: "ztarget",
            description: "Z-Targeting lock-on & context camera (OoT-style) for Groot",
            author: "John Esleyer",
            path: "../groot-plugin-ztarget",
            repo: "https://github.com/JohnEsleyer/groot-plugin-ztarget",
        ),
    ]
)
```

- `path`: local dev path, relative to `groot/Cargo.toml`. All plugins are siblings in `012-groot/` so `../groot-plugin-<name>` from `groot/` points to `../groot-plugin-<name>` (`groot/src/bin/cli.rs:952` reads `../groot-plugins/index.ron` when `cwd==groot/`).
- `repo`: GitHub URL used by `groot plugin add <name>` (`groot/src/bin/cli.rs:994` prefers `repo` → `git = "<repo>"`, fallback to `path`). This is why you see `../` — Cargo `path` deps are file-system relative, while `repo` is for remote installs.

## Adding a Plugin

To register a new plugin, add an entry to `index.ron`:

```ron
(
    name: "your-plugin",
    description: "What your plugin does",
    author: "Your Name",
    path: "../groot-plugin-your-plugin",        // local dev (relative to groot/Cargo.toml)
    repo: "https://github.com/YourName/groot-plugin-your-plugin", // GitHub install
)
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [groot-plugin-audio](https://github.com/JohnEsleyer/groot-plugin-audio) | Audio synthesizer & sound effects |
| [groot-plugin-gizmos](https://github.com/JohnEsleyer/groot-plugin-gizmos) | 2D/3D debug shape drawer |
| [groot-plugin-ztarget](https://github.com/JohnEsleyer/groot-plugin-ztarget) | Z-Targeting lock-on & context camera (OoT-style) |
| [groot-plugin-kinematics](https://github.com/JohnEsleyer/groot-plugin-kinematics) | Action-adventure 3D kinematic character controller |
| [groot-plugin-combat](https://github.com/JohnEsleyer/groot-plugin-combat) | Melee swept hitboxes, shield blocking, and damage protocol |
| [groot-plugin-skeletal](https://github.com/JohnEsleyer/groot-plugin-skeletal) | Skeletal animation, bone sockets, and blend trees |
| [groot-plugin-navmesh](https://github.com/JohnEsleyer/groot-plugin-navmesh) | 3D NavMesh spatial pathfinding and AI steering |
| [groot-plugin-gamestate](https://github.com/JohnEsleyer/groot-plugin-gamestate) | Zelda-style flag registry, dungeon inventory, and save system |
| [groot-plugin-dialogue](https://github.com/JohnEsleyer/groot-plugin-dialogue) | Typewriter dialogue, NPC choices, and cutscene text sequences |
| [groot-plugin-audio-interactive](https://github.com/JohnEsleyer/groot-plugin-audio-interactive) | Dynamic background crossfading and Ocarina melody sequence detection |
| [groot-plugin-fps-camera](https://github.com/JohnEsleyer/groot-plugin-fps-camera) | First-person look, head bob, and camera trauma for Groot FPS |
| [groot-plugin-fps-movement](https://github.com/JohnEsleyer/groot-plugin-fps-movement) | Quake/Source style FPS character movement for Groot |
| [groot-plugin-ballistics](https://github.com/JohnEsleyer/groot-plugin-ballistics) | Hitscan, projectiles, spread and recoil for Groot FPS |
| [groot-plugin-viewmodel](https://github.com/JohnEsleyer/groot-plugin-viewmodel) | Dual-FOV weapon viewmodel and sway for Groot FPS |
| [groot-plugin-decals](https://github.com/JohnEsleyer/groot-plugin-decals) | Bullet holes, scorch marks and blood decals for Groot FPS |
| [groot-plugin-particles](https://github.com/JohnEsleyer/groot-plugin-particles) | GPU sparks, shell casings and muzzle flashes for Groot FPS |
| [groot-plugin-perception-ai](https://github.com/JohnEsleyer/groot-plugin-perception-ai) | Sensory AI vision cones, hearing and cover for Groot FPS |
| [groot-plugin-spatial-audio](https://github.com/JohnEsleyer/groot-plugin-spatial-audio) | 3D positional audio and room occlusion for Groot FPS |
