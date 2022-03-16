  <h1 align="center">Command-Line Game</h3>

<br />

### About The Project

* This project started with the motivation to create a command-line game in Python using GraphWin Objects.
* The user starts the game from a room and has to move into other rooms to gather objects in his inventory that will help solve a puzzle.
* To win the game, the user has to go to a specific room with specific objects inside his inventory.
* Once the puzzle solved, a score is calculated based on the user's performance. The highest score (100%) can be reached if the user manages to solve the game with the least amount of commands and the least items in his inventory.

<br />

### Usage
Before running `Game.py`, make sure to put `space.png` and `rooms_page_background.png` in the same folder. 

<br />

### Code Specifications
* Code Input: 
	* Command entered by the user: `go [direction]`, `get [object]`, `look [room]` or `view inventory`.

* Code Output:
	* A change in position/room with a message noticing it if the user’s command is `go`.
	* A message with a description of the object the user picked up if his command is `get`.
	* A message with the description of the room and the objects in this room if the user’s command is `look`.
	* A list of all the objects the user picked up if his command is `view inventory`
	* A message noticing the user won together with his score if the user has solved the puzzle.

* Relations:
	* For the `go` command:
		* Going North: x, y = x-1, y+0
		* Going South: x, y = x+1, y+0	
		* Going East: x, y = x+0, y+1
		* Going West: x, y = x+0, y-1

	* For the `get` command:
		* Inventory = Inventory + Append any new object

	* When the user wins:  
		* Score (%) = 9/(number of commands entered by user)*60+3/(number of objects in inventory)*40

<br />

### Pseudo-Code

**Import the graphics library**

**Functions:**
* F1 to F6: Create a function for each room (6) that will be called every time the user enters the room. 
	* Each function will return:
		* A small description of the room
		* A list of the objects that are in the room
		* A list of the possible directions to go
		* A list of the possible rooms to look at (nearby rooms) once in this room.

* F7: Create a function that receives direction and possible directions as parameters and validates if the direction the user enters as a command is possible.
	* If the direction is not in the list of possible directions:
		* Return false (it is not possible to go in this direction)
		* Otherwise return true (it is possible to go in this direction)

* F8: Create a function that receives the room and possible looks and validates if the room the user wants to look at is possible.
	* If the room is not in the possible looks list:
		* Return false (looking at this room is not possible)
		* Otherwise return true (looking at this room is possible)

* F9: Create a function to validate if the user entered a valid command: `go [direction]`, `get [object]`, `look [room]` or `view inventory` that receives the command as a parameter.
	* Split the command by space 
	* If there are less than 2 separate words:
		* Return false (the command is not valid)
	* If the first word of command is `go`, `get`, `look` or the whole command is `view inventory`:
		* Return true (the command is valid)

* F10: Create a function that will manage the go command by changing the position of the user depending on his direction thanks to D2. This function will receive as inputs the current position of the user and the direction the user wants to go.
	* It will return the following outputs with the following relations depending on the direction chosen:
		* Going North: current position in x, current position in y = current position in x - 1, current position in y + 0
		* Going South:  current position in x, current position in y = current position in x + 1, current position in y + 0
		* Going East:  current position in x, current position in y = current position in x + 0, current position in y + 1
		* Going West: current position in x, current position in y = current position in x + 0, current position in y - 1

* F11: Create a function that receives the graph window as a parameter and gets the command entry of the user on a window. 
    * Create an entry box at point (550, 90) with width 30
    * Set its size to 10
	* Set its fill to “white”
	* Set the text color inside the entry box to “black”
	* Draw the entry box on the window

	* Create an infinite loop:
		* Get the key pressed by the player
		* If the key is “enter”/”return”:
			* Close the graph window received as a parameter
			* Return the text that the user entered in the entry box

F12: Create a function that takes the player’s current position as a parameter and converts it into coordinates on the window to display a green dot over a map to indicate its current position.
If player’s current position is [0, 1]:
	Return the coordinates (347, 154)
If the player’s current position is [1, 0]:
	Return the coordinates (265, 222)
If the player’s current position is [1, 1]:
	Return the coordinates (347, 222)
If the player’s current position is [1, 2]:
	Return the coordinates (429, 222)
If the player’s current position is [2, 1]:
	Return the coordinates (347, 286)
If the player’s current position is [2, 2]:
	Return the coordinates (429, 286)

F13: Create a function that displays a welcome page when the user starts the game with an introduction message.
Create a 670x440 GraphWin titled “Adventure Game”
Draw image “space.png” at point (335, 220)
Create a welcome message text at point (335, 80)
Set color to welcome message to “white”
Draw welcome message
Create a “Start Here” text at point (550, 370)
Set its text color to “goldenrod”
Set its style to “bold”
Set its size to 25
Draw “Start Here” text

Create an infinite loop:
	Get the position of the mouse click when the user clicks on the screen
	If the X coordinate of the position is between 550 and 670 including and the Y coordinate is between 350 and 380 including:
		Break out of the infinite loop

Close the graph window

F14: Create a function that displays an instruction page after the user starts the game.
Create a 670x440 GraphWin titled “Adventure Game”
Set the window background to “black”
Create a text “Instructions” at point (335, 30)
Create a text with the actual instructions at point (335, 200)
Create a text prompting the user to click on the screen at point (335, 400)
Set the first text color to “red”
Set the second text color to “goldenrod”
Set the third text color to “white”
Set the first text size to 20
Set the second text size to 13
Set the third text size to 15
Draw the first text on the window
Draw the second text on the window
Draw the third text on the window

Wait for the user to click on the screen
Once the user clicks on the screen, close the window

F15: Create a function that receives a message and the player’s current position as parameters and displays the main interface where the user will be typing his commands and will be receiving feedback on these. This interface will display a map with a green dot corresponding to the current position of the user thanks to F12. 
Create a 670x440 GraphWin titled “Adventure Game”
Draw image “rooms_page_backgroud” at point (335, 220)
Create triangle with coordinates (335, 21), (88, 374), (582, 374)
Create rectangle1 with coordinates (293, 205), (376, 270)
Create rectangle2 with coordinates (293, 139), (376, 205)
Create rectangle3 with coordinates (293, 332), (376, 270)
Create rectangle4 with coordinates (293, 205), (214, 270)
Create rectangle5 with coordinates (375, 205), (455, 270)
Create rectangle6 with coordinates (375, 270), (455, 332)

Create a list of shapes which contains all 6 rectangles and the triangle
For each shape in the list of shapes:
	Set fill to “SlateGray3”
	Set the fill only to the triangle to “Slategray”
	Set the outline to “goldenrod”
	Set width to 1
	Set the width only to the triangle to 3
	Draw each shape on the window

Create text “Cockpit” at point (333, 152) (T1)
Create text “Main Cabin” at point (333, 218) (T2)
Create text “Systems Room” at point (253, 218) (T3)
Create text “Pilot Room” at point (413, 219) (T4)
Create text “Cargo Room” at point (333, 281) (T5)
Create text “Engine Room” at point (413, 282) (T6)
Create a text asking the user about their next move at point (546, 46) (T7)
Create a text “Press Enter to quit” at point (485, 66) (T8)
Create a text with the message that was received as a parameter at point (146, 76) (T9)
Add all text variables to a list 

For each text message in the list of text messages:
	Set the text color to “white”
	Set the text size to 8
	Draw the text message on the window

Set only the size of T7 to 13
Set only the size of T8 to 8
Set only the size of T9 to 10

Assign to X and Y the coordinates of the current position of the player by calling the function which calculates them
Create a circle which displays the player’s position at point (x-15, y+25) with radius 10
Set its fill to “forest green”
Draw the circle on the window

Return the result of the function which gets the player’s input as text

Dictionaries:
D1: Create a dictionary that takes as a key the position of the user and calls F1 to F6 depending on the position. 

D2: Create a dictionary that takes as key a direction “north”, “south”, “east” or “west” and as value the change in coordinates it involves as x and y. 

D3: Create a dictionary that takes as a key the name of the object and as value the description of this object.

 D4: Create a dictionary that takes as a key the name of the room and as value the description of this room.


Main:
F16: Create the main function.
Call F13 and F14 to display the welcome and instruction screens.
Set all variables to starting conditions (empty inventory, starting position with possible rooms to go to and look at, action count to 0…)

Create a while loop that stops when the user wins or presses “enter”:
Get the user’s command using F11.
Check if his command is valid using F9, if not warn him it is not.

If the user’s command is `go`:
Get the direction inside the command. 
Check if the direction is possible using F7. If it is not possible, warn the user.
Get the new current position using F10.

If the user’s command is `look`:
	Get the room inside the command.
	Check if it is possible to look at that room using F8. If it is not possible, warn the user.
	Display the description of the room using D4

If the user’s command is `get`:
	Get the object inside the command.
	Check if the object is in the room using F1 to F6 and if it is not already in the inventory.
	Append the new object to the inventory. 

If the user’s command is `view inventory`:
	Display the list of objects inside the inventory or a message saying the inventory is empty in case it is. 

If the user is in Room 6 with the correct objects to solve the puzzle:
	Display the user has won the game and his score using the relation:
Score (%)  = 9/(number of commands entered by user)*60+3/(number of objects in inventory)*40


Print the current action in a file

End the while loop
Close the file

Call the main
