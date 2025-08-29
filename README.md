# BezierCurveVFX

**BezierCurveVFX** is a Lua module that provides a flexible system for generating and animating Bezier curve-based visual effects.  
It is useful for smooth particle/projectile motion, dynamic effects such as energy trails, experience orbs, guided missiles, or any situation requiring curved paths.

---

## Features
- Dynamic target tracking with adaptive smoothing.  
- Randomized curve generation for natural, non-linear motion.  
- Custom control points and offsets for precise curve shaping.  
- Speed-based or duration-based curve progression.  
- Lightweight implementation optimized for `RunService.Heartbeat`.  

---

## Requirements
- Lua environment.  

---

## Installation
1. Copy `BezierCurveVFX.lua` into your project (e.g., inside `ReplicatedStorage` for shared access).  
2. Require it from your script:

```lua
local BezierCurveVFX = require(game.ReplicatedStorage.BezierCurveVFX)
```

---

## Usage

### Basic Example
```lua
local curveVFX = BezierCurveVFX.new(
    attachment, -- Starting attachment
    target,     -- Target (Vector3, BasePart, or Attachment)
    {
        keepTrack = true,
        duration = 2,
        randomization = 0.3
    }
)

curveVFX:start()
```

---

## Configuration Options

| Setting            | Type         | Default | Description |
|--------------------|-------------|---------|-------------|
| `randomOffsets`    | `boolean`   | `false` | Adds small random offsets to curve points. |
| `offsets`          | `{Vector3}` | `{}`    | Custom offsets applied to intermediate control points. |
| `points`           | `{Vector3}` | `nil`   | Explicitly defined control points. |
| `keepTrack`        | `boolean`   | `false` | Continuously follows moving targets. |
| `duration`         | `number`    | `2`     | Time for the curve to complete (seconds). Ignored if `speed` is set. |
| `speed`            | `number`    | `nil`   | Moves at a constant studs per second, overriding `duration`. |
| `randomization`    | `number`    | `0.3`   | Degree of curve waviness (0.1 = subtle, 1.0 = highly irregular). |
| `adaptiveSmoothing`| `boolean`   | `true`  | Smooths adjustments when following moving targets. |

---

## Public API

```lua
:start()                   -- Start animating along the curve
:stop()                    -- Stop the animation
:updateSettings(settings)  -- Apply new settings during runtime
:updateTarget(target)      -- Change the target while running
:getPreviewPoints(res)     -- Return curve points for visualization/debugging
:destroy()                 -- Cleanup resources
```

---

## Example Demonstration

The module includes a built-in example that creates two anchored parts and animates a glowing orb along a Bezier curve between them:

```lua
local BezierCurveVFX = require(game.ReplicatedStorage.BezierCurveVFX)
BezierCurveVFX.createExample()
```

---

## Example Use Cases
- Experience orbs moving towards the player.  
- Magic or elemental projectile paths.  
- Guided missiles that follow moving targets.  
- Curved particle trails for environmental or combat effects.  
- Custom-defined cinematic motion paths.  

---

## Languages
- **Primary Language**: Lua.  

---

## License
This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute it in both personal and commercial projects.  
