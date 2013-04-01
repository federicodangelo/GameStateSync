GameStateSync
=============

Simple game state synchronization across multiple devices

The main purprose of this library if to help keep game state synchronized across multiple devices, without the need to have a persistent game server connection.

To do this, the game stores the last known server state and the current game state, and when the server can be reached it synchronizes the changes.

If another devices made changes to the game state, the library downloads the new server state from the server, merges it with the changes mades since the last syncrhonization, and uploads the new game state to the server.

To merge logic used can be defined on a field level, for example:
- if you have an "experience" field, you can choose to always keep the highest value.
- if you have an "money" field, you can choose to keep the delta value since the last syncrhonization, so if the player spent 2 dolars since the last syncrhonization, then the new value will be the "new server money value" minus 2 dolars.
- if you have an "items unlocked" field, which contains IDs of unlocked items, you can choose to always merge the values, so no item is ever lost.

The server only needs to implement some very basic functions to retrieve / store the last server state, and some helper functions used to optimize data transfer.

The project is currently in design phase, the design is being made using the ArgoUML tool, available at http://argouml.tigris.org/