# Games
Test






##Code Specifications


Goal: Create a game where the user goes from a room to another to gather objects and solve a puzzle.

Code Input: Command entered by the user: “go [direction]”, “get [object]”, “look [room]” or “view inventory”.

Code Output:
	A change in position/room with a message noticing it if the user’s command is “go”.
	A message with a description of the object the user picked up if his command is “get”.
	A message with the description of the room and the objects in this room if the user’s command is “look”.
	A list of all the objects the user picked up if his command is “view inventory”
	A message noticing the user won together with his score if the user has solved the puzzle.

Relations:
For the go command:
Going North: x, y = x-1, y+0
Going South: x, y = x+1, y+0
Going East: x, y = x+0, y+1
Going West: x, y = x+0, y-1

For the get command:
Inventory = Inventory + Append any new object

When the user wins:
Score (%) = 9/(number of commands entered by user)*60+3/(number of objects in inventory)*40
