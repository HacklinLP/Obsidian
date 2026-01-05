File structure breakdown:
- **Content**: This is the most important folder for visuals and audio. It contains a `.mgcb` file. It's where you track all your "Assets" - like the Pikachu sprites, background music and fonts.
- **Core**: This usually contains the "engine" parts of your game that don't change all that much throughout playing. This might include something like a camera class, global settings file OR custom input managers (keyboard/controller logic)


## 📂 Project Folder Breakdown

### 🏗️ Core

_The foundation classes that provide the "engine" functionality for the game._

- **Base/Sprite.cs**: The parent class for all visual objects; handles position, texture, and the basic `Draw()` method.
    
- **ContentFacade.cs**: A "Facade" pattern that provides a simplified interface for other classes to request game assets.
    
- **InputFacade.cs**: Simplifies interaction with MonoGame’s input systems (Keyboard/Mouse), acting as a single point of contact for input checks.
    

### 🧠 States

_Implements a State Machine to manage different screens or game modes._

- **Base**: Contains the template or abstract class that all game states must inherit from.
    
- **StartScreenState**: Logic for the initial menu or "Press Start" screen.
    
- **PlayingState**: The "Main" state where the active gameplay logic (Pikachu's movement, collisions) occurs.
    
- **PauseState**: Logic for when the game is frozen/paused.
    
- **GameOverState**: Logic for the end-of-game scenario.
    

### 🛠️ Services

_Modular systems that provide specific functionality across the entire application._

- **InputServices**: Logic for interpreting raw input into game actions.
    
- **ContentService**: Handles the efficient loading, storage, and unloading of textures and sounds.
    

### 📜 Interface

_Defines "contracts" for classes to ensure modularity._

- **IPlayerMovementInputService.cs**: An interface (prefixed with `I`) that defines exactly what methods a movement service must have, allowing you to swap input methods (like Keyboard vs. Controller) without breaking the player logic.
    

### 👾 Object

_Where the actual game entities live._

- **PlayerSprite.cs**: This is the Pikachu class; it inherits from `Sprite.cs` but adds specific logic for the player character, such as movement speed or gravity.
    

### 📎 Extensions

_Utility methods that add functionality to existing MonoGame classes._

- **SpriteBatchExtensions.cs**: Adds custom "shortcut" methods to the standard `SpriteBatch` (e.g., drawing shapes or specific text effects not included in MonoGame by default).
    

---

## 📄 Main Entry Files

- **Game1.cs**: The "Heart" of the game. In this architecture, it is kept slim—mostly just initializing the `StateManager` and telling it which state to start with.
    
- **Program.cs**: The entry point that launches the application.