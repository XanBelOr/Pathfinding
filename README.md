# Pathfinding
A user-friendly datapack library that lets any entity be able to pathfind using A*.

# Pathfinding Datapack for Minecraft

## Overview
This Pathfinding Datapack introduces an innovative and customizable solution for navigating entities within Minecraft. It is designed with a focus on boss entities and controlled scenarios, providing a safer and more optimized pathfinding experience. While this system presents a notable improvement, it's essential to understand that pathfinding with datapacks in Minecraft has its limitations due to the intensive nature of the process. However, this datapack (somewhat) addresses these challenges with a unique approach to minimize performance impact.

## Features
- **Performance-Optimized Queue System:** Implements a queue system for pathfinding tasks, processing one path at a time to significantly reduce lag.
- **Duplicate Request Prevention:** Prevents entities from being queued multiple times for pathfinding until their current path is resolved. Active paths can be updated for dynamic routing.
- **Configurable Pathfinding Parameters:** Offers extensive customization options, including entity height, maximum fall distance, step height, entity speed, cycles per tick, and maximum cycles for a path, the last two adjustable in the datapack's configuration file.
- **Adaptive Pathfinding with Failure Handling:** If the target is unreachable within the specified node search limit, the system will attempt to navigate to the next best node. The process aborts if no suitable nodes are found.
- **Dynamic Obstruction Detection:** Continually checks for obstructions along the solved path while the entity is in motion, allowing for real-time path adjustments.
- **Easy Initial Setup:** Users must remember to initialize the system by calling the load function `function pathfinding:zzinternal/load` to ensure proper functionality.

## Customization Options
1. **Entity Height:** Defines how tall the entity is, in blocks.
2. **Max Fall Distance:** Specifies the maximum distance an entity is allowed to fall, in blocks.
3. **Step Height:** Determines the height an entity can step up, in blocks.
4. **Entity Speed:** Controls the speed at which the entity moves, in blocks per tick.
5. **Cycles per Tick:** Sets how many pathfinding searches are performed per tick, balancing between performance and responsiveness.
6. **Max Cycles for a Path:** Limits the total number of searches for a path, directing the entity towards the best available node if the target is not found within this limit.

## Usage Instructions
To effectively use this datapack, follow these steps to configure and initiate pathfinding for an entity:

1. **Set Entity Parameters**: Configure your entity's pathfinding characteristics using the following commands, executed as the entity:

```
# Define the step height in blocks
scoreboard players set @s pathfinding.step_height [STEP_HEIGHT]

# Set the entity's height in blocks
scoreboard players set @s pathfinding.entity_height [ENTITY_HEIGHT]

# Specify the maximum fall distance in blocks
scoreboard players set @s pathfinding.fall_distance [MAX_FALL_DISTANCE]

# Adjust the entity's speed in blocks per tick. This number can be a decimal.
data modify storage pathfinding:entity speed set value [ENTITY_SPEED]

# Queue a Path for Navigation: Determine your entity's destination and queue a path towards it:
# Example:
execute at @a[limit=1,sort=nearest] run function pathfinding:queue_path
```

Reminder: call the load function `function pathfinding:zzinternal/load` in your own load function.

This datapack makes use of the **[Iris](https://github.com/Aeldrion/Iris)** and **[gu](https://github.com/gibbsly/gu)** libraries. They are built in to the datapack and should not interfere with other instances of them.

Please DM "xanbelor" on discord for support, discussion, suggestions, or to report bugs.
