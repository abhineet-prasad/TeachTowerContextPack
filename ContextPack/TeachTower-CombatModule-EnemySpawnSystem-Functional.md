# Teach Tower-Combat Module-Enemy Spawn System-Functional

## Overview
The Enemy Spawn System is responsible for dynamically generating NPCs within the game environment.

## Requirements
- Spawn 8 slime monsters at an interval of 10 - 30 seconds.
- Spawn slime monsters only within a defined area range centered around a position.
- Spawning in water bodies & non-navigable zones is prohibited.
- Spawning should not cause a significant drop in the game’s frame rate.
- Spawning should not cause unnecessary allocations and deallocations of memory.
- Randomly choose the spawning positions and area range.
