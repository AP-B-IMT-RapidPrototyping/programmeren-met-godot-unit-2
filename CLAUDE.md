# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Godot 4.5 FPS (First Person Shooter) tutorial starter project. It provides a clean slate with a pre-built level environment and all necessary assets (CC0 licensed) to build a first-person shooter game. All gameplay scripts and functionality have been removed to serve as a starting point for educational tutorials. The project is based on a template by Kenney.

**Current State**: This is a stripped-down version containing only the level geometry, environment, and base assets. No player controller, enemies, weapons systems, or input actions are currently implemented.

## Running the Project

**Note**: This project requires Godot 4.5 (or compatible version). The project must be opened and run through the Godot editor.

- Main scene: `res://scenes/main.tscn`
- To run: Open the project in Godot Editor and press F5, or run from the editor's "Play" button
- The project uses the "Forward Plus" rendering method

## Project Structure

### Directory Structure

```
.
├── objects/           # Scene files for level geometry and objects
│   ├── cloud.tscn                # Decorative cloud objects
│   ├── platform.tscn             # Standard platform
│   ├── platform_large_grass.tscn # Large grass platform
│   ├── wall_low.tscn             # Low wall obstacle
│   └── wall_high.tscn            # High wall obstacle
├── scenes/            # Main game scenes
│   ├── main.tscn                 # Primary game level scene with environment
│   └── main-environment.tres     # Environment/lighting settings
├── models/            # 3D models (.glb files) - ready to import
│   ├── blaster.glb               # Weapon model
│   ├── character-enemy.glb       # Enemy character model
│   ├── character-player.glb      # Player character model
│   ├── cloud.glb                 # Cloud decoration model
│   ├── impact.glb                # Impact effect model
│   ├── platform*.glb             # Various platform models
│   └── wall*.glb                 # Various wall models
├── sprites/           # 2D sprites and animations (.tres)
│   ├── crosshair*.tres           # Crosshair UI sprites
│   ├── impact*.tres              # Impact effect sprite animations
│   └── muzzle*.tres              # Muzzle flash sprite animations
├── sounds/            # Audio files (.ogg)
│   ├── blaster_*.ogg             # Weapon sound effects
│   ├── enemy_explode.ogg         # Enemy destruction sound
│   ├── enemy_shoot.ogg           # Enemy attack sound
│   ├── footstep_*.ogg            # Player footstep sounds
│   ├── impact_*.ogg              # Impact/hit sounds
│   ├── jump_*.ogg                # Jump sounds
│   └── select.ogg                # UI selection sound
├── fonts/             # Font files
│   └── kenney-bold.ttf           # Kenney bold font
├── vector/            # Vector graphics
│   └── icon.svg                  # Project icon source
├── screenshots/       # Project screenshots
├── project.godot      # Godot project configuration
├── icon.png           # Project icon
└── README.md          # Project documentation
```

## Available Assets

### 3D Models (GLB Format)
All models are ready to be imported as scenes:
- **Characters**: `character-player.glb`, `character-enemy.glb`
- **Weapons**: `blaster.glb`
- **Effects**: `impact.glb`, `cloud.glb`
- **Environment**: Multiple platform and wall variants

### Sprite Animations (Tres Resources)
Pre-configured sprite animations for:
- **Crosshairs**: 4 variants (`crosshair-dot.tres`, `crosshair-outline-small.tres`, etc.)
- **Impact Effects**: 2 variants with animations
- **Muzzle Flash**: 2 variants with animations

### Audio Assets (OGG Format)
Complete set of game sounds:
- **Weapon**: Multiple blaster sound variants
- **Movement**: 6 footstep sound variations, 3 jump sound variations
- **Combat**: Impact sounds, enemy sounds
- **UI**: Selection sound

### Environment
The main scene (`scenes/main.tscn`) includes:
- Pre-configured environment with lighting (`main-environment.tres`)
- Level geometry built from platform and wall prefabs
- Properly configured WorldEnvironment and DirectionalLight3D
- Sky and fog settings

## Level Geometry Components

The `objects/` folder contains reusable scene components for level building:

### Platforms
- `platform.tscn` - Standard 10x10 platform
- `platform_large_grass.tscn` - Larger grass-textured platform

### Walls
- `wall_low.tscn` - Low wall for cover/obstacles
- `wall_high.tscn` - High wall for blocking

### Decoration
- `cloud.tscn` - Animated cloud decoration

All geometry pieces use StaticBody3D with CollisionShape3D for proper physics interaction.

## Tutorial Starting Points

This project is ideal for building tutorials on:

1. **First-Person Character Controller**
   - CharacterBody3D movement with WASD
   - Mouse look camera control
   - Jump mechanics
   - Gravity and physics

2. **Combat System**
   - Raycast-based shooting
   - Weapon switching
   - Hit detection
   - Visual effects (muzzle flash, impacts)

3. **Enemy AI**
   - Player tracking
   - Navigation
   - Attack behavior
   - Health system

4. **Audio System**
   - Sound effect management
   - Audio pooling
   - Footstep systems
   - Randomized sound playback

5. **UI/HUD**
   - Health display
   - Crosshair system
   - Weapon indicators

## Code Conventions

### Recommended GDScript Style
- snake_case for variables and functions
- Use `@export` decorator for inspector-editable variables
- Use `@onready var` pattern for scene tree node references
- Type hints where appropriate: `var speed: float = 5.0`
- Group related exports with `@export_group()` or `@export_subgroup()`

### Godot Best Practices
- Use CharacterBody3D for player controller (not RigidBody3D)
- Use RayCast3D for hit detection in shooting mechanics
- Implement autoload singletons for global systems (audio, game state)
- Use signals for communication between nodes
- Prefer built-in Godot input actions over direct key checking

## Technical Notes

### Rendering
- Project uses Forward Plus rendering method
- Default resolution: 1152x648
- MSAA 3D: 2x antialiasing enabled

### Physics
- Default gravity: Project default (9.8)
- Use CharacterBody3D for kinematic player movement
- Use StaticBody3D for level geometry (already implemented in platforms/walls)

### Input System
- No input actions are currently defined in `project.godot`
- Input map needs to be created based on tutorial requirements

### Asset Licensing
- All included assets are CC0 licensed (public domain)
- Assets by Kenney (www.kenney.nl)
