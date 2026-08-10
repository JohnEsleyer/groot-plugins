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
        ),
        (
            name: "gizmos",
            description: "2D/3D debug shape line drawer for Groot",
            author: "John Esleyer",
            path: "../groot-plugin-gizmos",
        ),
    ]
)
```

## Adding a Plugin

To register a new plugin, add an entry to `index.ron`:

```ron
(
    name: "your-plugin",
    description: "What your plugin does",
    author: "Your Name",
    path: "../groot-plugin-your-plugin",
)
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [groot-plugin-audio](https://github.com/JohnEsleyer/groot-plugin-audio) | Audio synthesizer & sound effects |
| [groot-plugin-gizmos](https://github.com/JohnEsleyer/groot-plugin-gizmos) | 2D/3D debug shape drawer |
