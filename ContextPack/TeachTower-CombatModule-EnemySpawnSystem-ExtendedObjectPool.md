TeachTower-Combat Module-Enemy Spawn System-Technical-Class ExtendedObjectPool
==================================================================================

What does it do?
----------------

The `ExtendedObjectPool<T>` class is a generic object pool implementation designed for efficient object reuse and management within Unity projects. It extends the functionality of Unity's `ObjectPool<T>` by providing additional features such as:

-   Tracking of active objects
-   Customizable actions upon object retrieval, release, and destruction
-   An option to prefill the pool to capacity

This class helps in reducing garbage collection overhead by reusing objects instead of creating and destroying them repeatedly, which is particularly useful for frequently instantiated objects like particles, bullets, or temporary UI elements in a game.

### Key features include:

-   Custom actions (`onGet`, `onRelease`, `onDestroy`) that can be executed when objects are retrieved, released, or destroyed.
-   Tracking of active objects, allowing for easy access and management of currently used objects.
-   An option to prefill the pool to a specified capacity upon creation, ensuring a number of objects are immediately available for use.
-   Methods to release all active objects and destroy all objects in the pool, aiding in cleanup and resource management.

### How to work with it?

To work with `ExtendedObjectPool<T>`, follow these steps:

1.  Initialization: Create an instance of the pool by specifying the type of objects it will manage (`T`), and providing a function to create new instances of `T`, along with optional actions for when objects are gotten from the pool, released back into it, or destroyed. You can also specify whether to prefill the pool, its initial capacity, and its maximum size.
2.  Retrieving Objects: Use the `Get()` or `GetPooled()` method to retrieve objects from the pool. `Get()` simply returns an object of type `T`, while `GetPooled()` returns a wrapper (`ExtendedPooledObject<T>`) that can automatically release the object back to the pool when disposed of. If an action was provided for `onGet`, it will be executed upon retrieval.
3.  Releasing Objects: When you're done using an object, release it back into the pool using the `Release(T item)` method. If the object is part of the active items list, it will be returned to the pool, and the `onRelease` action will be executed if provided.
4.  Managing Active Objects: You can access the list of currently active objects using the `GetActiveItems()` method. This feature is useful for managing or iterating over objects currently in use.
5.  Cleanup: Use the `ReleaseAll()` method to release all active objects back into the pool, or `DestroyAll()` to clear the pool completely. These methods are useful for cleaning up resources, for example, when changing scenes in a game.

By managing the lifecycle of objects more efficiently, `ExtendedObjectPool<T>` can help improve performance in Unity applications, particularly those with high object churn rates.