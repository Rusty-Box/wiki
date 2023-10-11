# Coin System

- Instead of a "total coin counter" that counts all coins collected across levels we have a coin counter per level
  - For example, a level that contains a total of 115 coins will show the counter as `x / 115`
- The coin counter will no longer be shown on the HUD when outside a level, i.e. while in a worldmap

- If Tux dies he looses all his coins in that level
  - If a checkpoint has been reached, Tux only looses the amounts of coins that he collected after activating the checkpoint
