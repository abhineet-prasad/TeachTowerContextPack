TeachTower-Combat Module-Enemy Spawn System-Technical-Class IWorldEntitySpawner
===================================================================================

What does it do?
----------------

The interface IWorldEntitySpawner specifies a method to asynchronously calculate a spawn position for entities considering several parameters:

-   `areaMask`: Filters potential spawn locations.
-   `searchRadius`: Defines the search area size for a spawn location.
-   `timeoutInSeconds`: Limits how long the search can take.
-   `snapToLayer`: Identifies the layer to align the spawn position with.
-   `offsetFromSnapLayer`: Adjusts the spawn position's vertical distance from the snapToLayer.
-   `cancellationToken`: Allows the operation to be canceled.

How to work with it?
--------------------

To effectively utilize the IWorldEntitySpawner interface in your application, follow these steps:

1.  Implement Interface: Implement the IWorldEntitySpawner interface in your class to define the asynchronous spawn position generation logic.
2.  VContainer Registration: Register the implementation with the VContainer framework to enable dependency injection. Use VContainer's registration methods within your container setup to map IWorldEntitySpawner to your implementation.
3.  Dependency Resolution: Once registered, resolve an instance of IWorldEntitySpawner through VContainer's dependency injection mechanisms wherever it's needed in your application.
4.  Invoke Method: Use the `GenerateSpawnPositionAsync` method by providing the necessary parameters (`areaMask`, `searchRadius`, `timeoutInSeconds`, `snapToLayer`, `offsetFromSnapLayer`, and `cancellationToken`) to asynchronously obtain a spawn position.
5.  Handle Results: Process the method's return value, a tuple `(bool success, Vector3 position)`, to determine the next steps based on the success of the spawn position generation.

By following these guidelines, developers can seamlessly integrate asynchronous entity spawning capabilities into their Unity projects, enhancing gameplay dynamics and interactivity.