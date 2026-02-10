# DESIGN

## Screens Architecture

The State class was borrowed from the original cavern.py, which maps integer values to the three different states/screens the game can be in.

The main App class handles whenever this state changes, and ensures that the current screen is set to whichever state is currently active via creating a new corresponding Screen object.

As described in the assignment document, each screen creates and owns the Game object, and determines if the player needs to spawn in or not. Each screen also has its own update and draw function, capturing the current input state as passed by the input manager.

## Input Design

A dataclass helper, InputState (admittedly didn't know what a dataclass was in python before this assignment) assigns a boolean to set inputs the user can make. More specifically, this game only cares about left, right, jump_pressed, fire_pressed, fire_held, and pause_pressed, and assigns these names to each input for better readability and clarity.

Another class, InputManager, checks the keyboard input via the pgzero keyboard global variable, to see which booleans from InputState should be turned on/off. This will get called each frame from App, and the input state will be passed down to the current screen from app as well.

## How "Pause" works

The pause feature is relatively straightforward. In PlayScreen, a boolean is initialized which handles the screen being paused or not. This is only initialized in PlayScreen to ensure the game can't be paused on a game over, or in the menu.

On each frame update, the PlayScreen makes sure this pause boolean is turned off before calling the game update. Furthermore, if the pause boolean is True, some text "PAUSED" will be drawn on the screen.