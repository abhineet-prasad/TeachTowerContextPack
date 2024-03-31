# TeachTower - Code Practices

## Code Structure
- Use **PascalCase** for all folder names.
- Never use spaces, Unicode character, or other symbols in folder names.
- There should be no empty folders.

### Modules:
- Any new feature should be added as a module under the **Modules** folder.
- The module name should clearly describe the feature it is implementing.
- Each module should contain its introductions to the game world in its own scene.
- Each module folder should contain individual folders for all the scripts, data files, scriptable objects, prefabs, scenes, and animation files respectively.
- The **Scripts** folder should be further broken down into **Runtime** and **Editor** folders for Runtime and Editor scripts respectively.
- All scripts should be added to folders inside Runtime or Editor folders to allow for automatic creation of assembly files.
- Every class, enum, interface, etc., should be in its own file unless its scope is restricted to one class.

## Naming Conventions
- **GameObjects**: Use PascalCase for GameObject names. These names should provide an indication of the object's function or purpose.
- **Scripts**: Use PascalCase for script file names. These should be short, concise, and descriptive of the functionality they contain.

### Variables:
- Use **camelCase** for instance variable names.
- All non-boolean variable names must be clear, unambiguous, and descriptive nouns.
- All boolean variables should ask a question, for example, `isReady` instead of `ready`.
- All variable names must not be redundant with their context as all variable references in the class will always have context.
- Use **PascalCase** for public variables, **camelCase** prefixed with an underscore for private variables, and **camelCase** for local variables.
- All Serializable variables should have a description in their `[Tooltip]` fields that explains how changing this value affects the behavior of the script.
- Constant variables should be named using **SCREAMING_SNAKE_CASE**.

### Functions:
- Use **PascalCase** for function names. They should describe the action performed by the method.
- All functions should be verbs.
- Functions returning bool should ask questions.
- Any function that handles an event should start with `On`.

### Parameters:
- Use **camelCase** for parameter names. They should be descriptive of what information is being passed into the method.

### Events:
- Use **PascalCase** followed by 'Event' suffix for event names.

### Animation and Animator States:
- Use **PascalCase** with a description of the action for Animator state names.

### Shaders:
- Use **PascalCase** with a suffix of Shader for Shader names.

### Materials:
- Use **PascalCase** with a suffix of Mat or Material for Material names.

## Abstractions
- Use Scriptable Objects to abstract out configurable parameters for a class. This helps in exposing the configuration to the UI and allows for lesser changes in class files when config values are modified and therefore, helps with versioning.

## Readability
- Declare each variable in a new line.
- Always use the access modifier for each member/member function.
- Use the following order when defining functions `(access modifier)(method modifier)(return type) (Function name)`, for example, `public override void DoSomething();`
- Start braces from a new line.
- Use braces for if conditions even if it has only one line.
- Do not use `var` when the type is not apparent from the right side of the assignment.
- Favor explicit boolean comparisons over negation operators, for example, `if(IsRight == false)` instead of `if(!IsRight)`.
- Use a single space after a comma between function arguments.

## Performance Optimization
- Usage of **Object Pools** should be encouraged instead of instantiating and destroying game objects during runtime.
- Avoid using `'Camera.main'` in every frame, cache it once and use.
- Recommend caching transform and gameObject if frequent calls are made, since they are extern calls and therefore, slow.
- Heavy computations should not be performed inside `Update()` method. Alternatives like Coroutines or separate threads should be recommended.
- Use of layers should be considered for reducing unnecessary rendering.
- Strict memory management should be observed by checking unnecessary allocations and deallocations. Make sure garbage collection isn’t invoked often.
- Inspect the usage of Coroutines: Verify if there's any misuse of 'yield return null', 'yield return new WaitForEndOfFrame()', and 'yield return StartCoroutine()' in the codebase.
- Evaluate Garbage Collection: Check for unnecessary instantiation in the `Update()`, `FixedUpdate()`, or `LateUpdate()` methods and point out any component that might be causing a memory leak.
- Overdraw and Transparency inspections: Verify if there are any unnecessary shaders or textures being rendered, especially in UI elements.
- Check Physics Simulation: Pay attention to any expensive physics simulation that could harm the performance, including `OnCollision()` and `OnTriggerEnter()` functions.
- Examine Script performance: Check for any misuse of `Update()`, `FixedUpdate()`, `OnGUI()`, or any other frequently called methods and recommend more efficient message-sending options where possible.
- Animation and Graphics: Look out for any misuses of Animator components, multiple Camera renderings, improper Light settings, and inefficient usage of Meshes or Textures.
- Evaluate Asset Loading: Check for improper use of `Resources.Load()` and any case of synchronous loading that could cause performance hiccups.
- Evaluate order of mathematical operations and suggest the most performant one.

## Testability
## DB Access
## 3rd Party Libraries
- Add 3rd party libraries in the Jenga3rdPartyAssets submodule.
