# Cavern Refactor
## CSCI 4160 - Interactive Computing

The main goal of this assignment was to refactor a pygame remake of Bubble Bobble (found <a href="https://github.com/Wireframe-Magazine/Code-the-Classics/tree/master/cavern-master">here</a>) to have a different structure without changing gameplay.

---

### How to run the game

Installing Requirements
```Shell
python -m venv venv
./venv/scripts/activate # Windows
pip install -r requirements.txt
```

Running the main script
```Shell
python cavern_refactored.py
```

### Architectural Changes

Three different screens were implemented as per the assignment outline:
- MenuScreen
- PlayScreen
- GameOverScreen

These are each their own individual class, with their own initialization of the Game object, an update() function, and a draw() function. The Game object takes an optional Player argument, which is used to determine if the player is spawned on each screen or not (for example, don't spawn them in the background of the menu screen, but spawn them in the main play screen)

All player inputs are now handled by an InputManager class, which returns an state for what inputs are currently being pressed. This state uses an InputState helper class, which holds booleans for true/false values on each key input (like in godot!).

All actors (player, robot enemy, other entities etc) were left unchanged in the refactor.