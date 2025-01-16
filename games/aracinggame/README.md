# Racing Game

A simple Racing Game where you drive rounds on a track and try to reach a highscore in form of the best time to complete.

## Dependencies

+ python
+ pygame


## How to Run

+ Run `python game.py`

## Controls

+ Esc to leave the current scene/End the game in the Main Menu
+ W/S to move in the menu, options and Enter to confirm selection
+ To drive you can steer with A/D and use W to drive forwards and S to brake/reverse
+ To change gears you either use Q/E to go one down/up or just the numbers 1-6

## Rules

+ If you complete 3 rounds while passing the checkpoints you will end the game and can enter your name if you reached a new highscore
+ If you drive into the lake or mountains your car crashes resulting in a game over
+ If you drive on the grass you will get slowed down


## Files and functions

+ `game.py` : main loop, main menu, options, highscores, gamestates, help functions
  + `main_menu(screen, lastButton)`: draws the buttons you can press, chose the next scene, title
  + `options(screen, lastButton)`: draws options, lets you chose between them and adjust them
  + `highscore(screen, lastButton)`: loads the highscores, draws them, return to main menu with exit
  + `leave(screen, lastButton)`: used when exit button in the main menu is pressed
  + `draw_Text(screen,font,color,text,position)`: help function to call for drawing
  + `convert_Time(miliseconds)`: help function for the correct display of score time
  + `write_highscores(highscores)`: help function so save highscore
  + `read_highscores()`: help function to see highscores
  + `write_ghost_car(event_array_with_ticks)`: help function to save the best driver
  + `read_ghost_car()`: help function to call to get the ghostcar
  + `game(screen, lastButtons)`: gamestates, render functions, checkpoints, collision, ghostcar
    + `check_Ground(car_position)`: checks collision map for color of ground car is on to reduce speed or game over
    + `drive_Ghost(screen,in_start_phase)`: uses help functions to let the saved data display a 2nd player that is the best driver
    + `create_Checkpoint(next_checkpoint)`: creates the next checkpoint on the map
    + `check_Checkpoint(car_position, checkpoint)`: checks if the car collides with the checkpoint
    + `render`functions: update the screen according to input/variables
      + `draw_Roundscale(screen,background,needle,scale,shown_value,max_value,offset_bottom_right)`: draws the roundscale and needle as needed
    + `start_Timer(set = 0)`: starts the timer
    + `not_started(screen,pressed_keys)`: default gamestate loads everything at the start
    + `input_expected(screen,pressed_keys)`: draws text,waits for player to press Space
    + `start_timer(screen,pressed_keys)`: stops you from pressing s, rpm can already go up, show timer going down
    + `show_go(screen, pressed_keys)`: starts timer, draws GO
    + `game_running(screen, pressed_keys)`: lets you drive around, checks for ground, checkpoints, gear
    + `game_over(screen,pressed_keys)`: draws game over text, lets you restart
    + `game_finished(screen,pressed_keys)`: lets you type in name, shows highscores, puts you in if you are in top 10
  + `play_selection()` and other music functions : lets you play/stop the music/sound
+ `car.py` : definition of the car as a directory and all its movement

## Challenges

The Challenges are marked with HACKATHON CHALLENGE x in the code. Press ctrl+f and search in the code "game.py" to find the place to implement. The challenges don't need to be done in the order they appear, but are recommended in this order. <br />


### HACKATHON CHALLENGE 1

**Story🚗:** Someone stole the watch of the timekeeper! Build a new one for him so he can keep track of the scores again. <br />
  

**Task:** *Build a Timer.* A timer should be displayed on the screen when the game is started to keep track of the time score.

**Learning goal:** Think about how to convert a given time in milliseconds into the string format.

**File:** `game.py`

**Difficulty:** ⭐ <br />
<details>
  <summary>🔐 Hints</summary>
  <details>
  <summary>Hint 1</summary>
  
  - Use modulo (%) to extract the remainder when calculating milliseconds, seconds, and minutes.
  </details>

  <details>
  <summary>Hint 2</summary>
  
  - Use Python’s `str.format()` or `f-strings` to neatly format the time as MM:SS:MMM.
  </details> 
</details>  


### HACKATHON CHALLENGE 2

**Story🚗:** Oh No! Speedy McZoom broke his hand when he tried to stop the robber of the watch, and now he can't drive his car anymore. Help him by adding an automatic mode for the car so he doesn't need to shift gears anymore! <br />

**Task:** *Automatic mode.* Add an automatic mode to the car and display the text in the options' menu.  The automatic mode should shift gears based on speed so Speedy McZoom can continue driving without manual shifting.<br />
  

**Learning goal:** Understand how to use conditions to modify behavior based on state (automatic vs manual).

**File:** `game.py`,`car.py`

**Difficulty:** ⭐⭐ <br />

<details>
  <summary>🔐 Hints</summary>
  <details>
  <summary>Hint 1</summary>

  - Use a boolean variable (gearSetting) to manage the state (manual or automatic).
  </details>

  <details>
  <summary>Hint 2</summary>
  
  - Update the car’s behavior dynamically using conditional logic (if car['automatic']:).
  </details> 

  <details>
  <summary>Hint 3</summary>

  - Note the role of the function `automatic(car, set=None)` in `car.py` when generating the car object in `game.py`.  

  </details>

  <details>
  <summary>Hint 4</summary>

  - Use the speed to determine gear changes: 
    - Shift up if speed exceeds the maximum for the current gear. 
    - Shift down if speed falls below 50% of the maximum and gear > 1.
  </details> 

</details>  


### HACKATHON CHALLENGE 3.1

**Story🚗:** You are approached by the crazy scientist Dr. Warp Speedington. He invented a machine which allows investigators to look into the past. This would allow you to track the watch thief! He wants you to help him build his machine. First he needs you to build the module which can save and read the temporal aura of a car. He already built the part which captures it. <br />

**Task:** Write,save, and read the Temporal Car Aura <br />

**Learning goal:** Think about the file formats needed to save the Temporal Aura of the car. Also, creating logic for writing, saving and reading the Temporal Aura <br />

**File:** `game.py`

**Difficulty:** ⭐⭐⭐ <br />

<details>
  <summary>🔐 Hints</summary>
  <details>
  <summary>Hint 1</summary>

  - The "temporal car aura" is a way to record your actions during a game run.
  </details>

  <details>
  <summary>Hint 2</summary>

  - There are 2 parts in this Challenge. In Challenge 3.1.1, you write and save temporal car aura in the file of your choice and in Challenge 3.1.2, you read the temporal car aura.
  </details>
</details>

### HACKATHON CHALLENGE 3.2

**Story🚗:** Now that you can save the temporal aura Dr. Warp Speedington wants you to add the module which projects the temporal aura as a hologram back into the world so you can follow the tracks of the mysterious thief. <br />

**Task:** Implementing and running the ghost car using temporal car aura <br />

**Learning goal:**Implementing ghost car using the tick counts (pygame event) <br />

**File:** `game.py`

**Difficulty:** ⭐⭐⭐⭐ <br />

<details>
  <summary>🔐 Hints</summary>
  <details>
  <summary>Hint 1</summary>

  - There are two steps defined in the Challenge with additional docstrings for help.
  </details>
   <details>
  <summary>Hint 2</summary>

  - When implementation is complete, change use_ghost = True (from False) in the other end of #HACKATHON CHALLENGE 3.2.
  </details>
</details>




### Bonus Challenge 1

**Story🚗:** While driving the car, it gets confusing if the car is moving forward or backward. Help Dr. Warp Speedington in creating a module where it should display the Warning Message whenever the car is reversing while driving, so that you understand when you are going ahead and when backwards. <br />

**Task:** Warning message - Reverse Direction

**Learning goal:** Implementing a warning message in pygame when the player hits the reverse button to make the player understand that they are going in the wrong direction.  <br />


**File:** `game.py`

**Difficulty:** ⭐⭐

### Bonus Challenge 2

**Story🚗:** While chasing the watch thief, you notice several checkpoints on the track. Missing them could mean losing important clues! Help Dr. Warp Speedington create a module that reminds you when the car is near a checkpoint, so you don't miss checkpoints. <br />

**Task:** *Checkpoint Reminder*. Implement a feature to display a text reminder and a sound reminder when the car near a checkpoint. <br />

**Learning goal:** Think about why you need checkpoint reminder. Observe the generation of checkpoints and changes in the number of laps played. Look for underlying game rules and logic.  <br />

**File:** `game.py`

**Difficulty:** ⭐⭐
  
<details>
  <summary>🔐 Hints</summary>
  <details>
  <summary>Hint 1</summary>
  
  - Complete the function `check_near_Checkpoint()`.
  - Use Pygame's `pygame.font.Font` or `pygame.font.SysFont` to render text dynamically.
  - Add the sound into the file `games\aracinggame\sounds`
  </details> 
  
  <details>
  <summary>Hint 2</summary>
  
  - Think about what it means to be near a checkpoint.
  - Inspiration from the return value of the `check_Checkpoint()` function.
  - Note the coordinates of the checkpoints.
  </details>  
  
  <details>
  <summary>Hint 3</summary>

  - Pay attention to the handling of checkpoints and add appropriate if statement.
  </details> 
</details>

<details>
<summary> 🎉 Open when all challenges completed</summary>
  The machine of Dr. Warp Speedington works! A simulated ghostly car appears before you and starts driving away! Jump in car and follow him!
<details>
<summary>Open when you beat the ghost in a race</summary>
  You follow the car and it arrives in the garage of Speedy McZoom! When confronted he admits that he stole the watch to manipulate it and win the next race. To seem innocent he broke his hand. The police arrests him and you are celebrated as a hero for solving this devious theft!
</details>
</details>

<br>
+ EXTRA: you also can think about additional features to add




## Authors

+ Fabian Erbslöh
+ Ismail Yilmaz
+ Timon Hüsemann
+ Tobias Grzesch
