TeachTower-Combat Module-Enemy Spawn System-Technical-Class WorldEntitySpawner
==============================================================================

What does it do?
----------------

The WorldEntitySpawner class is responsible for:

-   Generating asynchronous spawn positions for entities on terrain.
-   Utilizing terrain data to find random valid locations.
-   Adjusting positions based on layer constraints and specified offsets.
-   Handling cancellations and exceptions gracefully.

How to work with it?
--------------------

### Initialize Dependency

Before using WorldEntitySpawner, ensure you have an instance of IMainEnvironmentTerrain. This interface represents the main environment terrain, which is a crucial part of generating spawn positions.

### Generate Position

Call `GenerateSpawnPositionAsync` with parameters: `areaMask`, `searchRadius`, `timeoutInSeconds`, `snapToLayer`, `offsetFromSnapLayer`, and `cancellationToken`.

### Return Value

Receives `(bool success, Vector3 position);` true and position if successful, false and default Vector3 otherwise.

### Cancellation and Error Handling

Supports operation cancellation and logs exceptions internally.

This class provides a way to asynchronously generate valid spawn positions for entities within a specified area of a terrain with support for grounding the position to a layer and handling errors gracefully.