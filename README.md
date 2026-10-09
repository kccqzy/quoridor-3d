# quoridor-3d
An implementation of the Quoridor game in 3D running in modern browsers (WebGL2).

All you need is a browser. No need to run a localhost server. The file is
self-contained and does not require asset files or network connections.
The browser here is just a secure executable platform to run the code.

## Rules

The game is played on a board with 9 by 9 squares. Vertically they are labelled
A through I. Horizontally they are labelled 1 through 9.

There are two players. Each player has a pawn. Initially the pawns are located
at A5 and I5. Each player in the beginning has ten unused fences located just
outside the 9x9 square grid. Each fence is 2x1 and slots in between the grids.
The goal is get the pawn to the other side. If the player starts at A5, then
ending anywhere from I1 to I9 would be the goal. Similarly if the player starts
at I5, ending anywhere from A1 to A9 would end the game. Whoever reaches first
wins.

Each turn the player can either move their own pawn or place a fence, but not
both.

When placing a fence, the user can position it either horizontally or
vertically. For example the 2x1 fence can be between E5 and F5, as well as E6
and F6. For another example the fence can be between E5 and E6, as well as F5
and F6. Fences may not intersect or overlap but they may touch. The fence may
not be fully or partially outside the grid. Each placement of a fence blocks
movement between two pairs of adjacent squares.

Once placed fences cannot be moved or removed.

Normally a pawn can be moved forward, backward, left or right by one space, but
not diagonally. For example if the current player is at E5, then the current
player can move to D5 or F5 or E4 or E6.

Exception 1: if the other player's pawn is located adjacent to the current
player's pawn, then the current player's pawn can move two spaces along that
direction. For example if the current player is at E5 and the other player is at
D5, then the current player can move to C5 or F5 or E4 or E6.

Exception 2: if the other player's pawn is located adjacent to the current
player's pawn, and there is a fence right beyond the other player, then the
current player can first move forward and then perpendicularly. For example
if the current player is at E5 and the other player is at D5 and there is a
fence between D5 and C5, then the current player can move to D4 or D6 (or of
course F5 or E4 or E6).

The most important rule: whenever a player places a fence, the player must
ensure that both players have a valid path from their current location to the
goal, no matter how long. Indeed a general strategy is to maximize the length of
the shortest path.
