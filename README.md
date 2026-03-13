# Synopsis: Clap-Controlled Flappy Bird Game Using SFML
## 1. Introduction
This program implements a **Flappy Bird–style game** developed in **C++ using the SFML (Simple and Fast Multimedia Library)**. The game introduces an innovative interaction method where the player controls the bird using **clap detection through a microphone** instead of keyboard input.

The program integrates **graphics rendering, physics simulation, audio processing, and real-time user interaction**. The player must guide the bird through moving pipes while avoiding collisions and gravity effects.
---
## 2. Objective

The objective of the project is to:

* Develop a **2D arcade game** using SFML.
* Implement **real-time microphone input** to detect claps.
* Use the clap sound as a **game control mechanism**.
* Demonstrate concepts of **object-oriented programming, physics simulation, and event handling** in C++.
---
## 3. Technologies Used

| Technology           | Purpose                                 |
| -------------------- | --------------------------------------- |
| **C++**              | Core programming language               |
| **SFML Graphics**    | Rendering game objects                  |
| **SFML Audio**       | Microphone input for clap detection     |
| **SFML Window**      | Event handling and window management    |
| **Standard Library** | Random number generation, vectors, math |
---
## 4. Game Concept
The player controls a **bird character** that must fly between vertically arranged pipes.
Key gameplay features:
* Gravity continuously pulls the bird downward.
* A **clap sound makes the bird jump upward**.
* Pipes move from right to left.
* The player scores points by passing through pipe gaps.
* The game ends if the bird hits a pipe or the ground.
---
## 5. Program Structure
The program is organized into several main components:
### 5.1 Constants
Several constants define the game environment:
* Window size (800 × 600)
* Gravity and jump force
* Pipe speed and gap
* Ground height
These constants help control the **game physics and layout**.
---
### 5.2 Game States
The program uses an **enumeration (GameState)** to control game flow.
States include:
* **Start** – Waiting for player input.
* **Playing** – Game is active.
* **GameOver** – Player loses and can restart.
This ensures proper control of game transitions.
---
## 6. Clap Detection System
A custom class **ClapDetector** inherits from `sf::SoundRecorder`.
### Purpose
It detects clap sounds from the microphone.
### Working Principle
The detector analyzes:
1. **Sound energy (volume)**
2. **High-frequency spikes**
Claps produce **sharp, high-frequency peaks**, unlike speech.
Conditions for clap detection:
* Sound must be loud enough.
* Must contain high-frequency variation.
* Must pass a cooldown period.
This prevents **false detection from speech or background noise**.
---
## 7. Bird Class
The **Bird** class represents the player character.
### Components
The bird is constructed from several graphical shapes:
* Circle → Body
* Rectangle → Wing
* Small circle → Eye
* Triangle → Beak
### Functions
* `reset()` – resets bird position
* `jump()` – applies upward force
* `update()` – applies gravity and movement
* `draw()` – renders the bird
The bird also rotates depending on velocity to simulate realistic motion.
---
## 8. Pipe Class
The **Pipe** class generates obstacles.
### Features
Each pipe consists of:
* Top pipe
* Bottom pipe
* Pipe caps
### Key Functions
* `update()` – moves pipes leftward
* `checkCollision()` – checks if bird hits pipe
* `passed()` – increases score
* `isOffscreen()` – removes pipes that leave the screen
Pipe gaps are generated randomly using a **random number generator**.
---
## 9. Main Game Loop
The `main()` function controls the game execution.
### Steps in Game Loop
1. Detect window events.
2. Detect clap input.
3. Update bird physics.
4. Spawn pipes at intervals.
5. Check collisions.
6. Update score.
7. Render all objects.
The loop runs at **60 frames per second**.
---
## 10. Scoring System
The player receives **1 point each time the bird passes a pipe**.
The score is displayed on screen using **SFML text rendering**.
---
## 11. Collision Detection
Collision occurs when:
* Bird intersects with a pipe
* Bird hits the ground
* Bird goes above the window
Collision detection uses **bounding box intersection**.
---
## 12. User Interaction
Controls are based on **clap sounds**:
| Game State | Clap Action  |
| ---------- | ------------ |
| Start      | Begin game   |
| Playing    | Bird jumps   |
| Game Over  | Restart game |
---
## 13. Graphics Rendering
The game includes:
* Blue sky background
* Green pipes
* Animated bird
* Ground platform
* Score display
All elements are rendered using **SFML shape objects**.
---
## 14. Conclusion
This project demonstrates how **audio input can be used as a game control mechanism**. By combining **C++, SFML graphics, physics simulation, and sound processing**, the program creates an engaging interactive game.
The project highlights practical applications of:
* Object-oriented programming
* Real-time input processing
* Game development concepts
* Multimedia programming with SFML
