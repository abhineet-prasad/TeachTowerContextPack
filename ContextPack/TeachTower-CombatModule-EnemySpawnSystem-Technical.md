# Teach Tower - Combat Module - Enemy Spawn System - Technical

## Technologies
- **Unity’s Navmesh:** For identifying valid spawn positions and avoiding prohibited zones.
- **Object Pooling:** To manage enemy character instances efficiently.

## Important Technical Decisions
- Utilize Unity’s navigation data to identify valid positions for spawning and avoid prohibited zones.
- Implement Object Pooling to instantiate and manage enemy characters efficiently, minimizing performance overhead.

## List of Classes
- **Class: ExtendedObjectPool<T>** - Enhances Unity's object pooling with lifecycle management for pooled objects. Supports initialization with capacity settings, optional prefilling, and comprehensive item management functionalities.
- **Interface: IWorldEntitySpawner** - Defines a contract for spawning world entities, focusing on generating viable spawn positions asynchronously.
- **Class: WorldEntitySpawner** - Implements IWorldEntitySpawner using terrain and navigation data to find suitable spawn points for entities. Includes robust exception handling and communicates outcomes via a tuple.
- **Class: WorldSpawnerLifetimeScope** - Sets up dependency injection for the world spawner module within the game's architecture, registering WorldEntitySpawner as a singleton service.

### Note
- WorldEntitySpawner related classes could either be used as a reference for a spawn service or modified for specific position/range functionality but may not meet the Enemy Spawn System requirements in their current form.
