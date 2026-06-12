# Redline Rising: Eclipse

HTML/JS top-down shooter. Can be run without dependencies, The sprite assets are completely optional and it was intentionally designed without them. Open `Redline_Rising_Eclipse.html` in a browser and play.

## Controls

- Left stick: move
- Right stick: aim / fire
- RESET button: restart current map
- MENU button: pick a map or set random map mode

## Maps

Four maps: WAREHOUSE, CORRIDOR, CROSSROADS, BUNKER. Each defines its own walls, player spawn, enemy spawns, patrol points, and sweep targets. Map mode is either fixed (pick one) or random (reroll on reset).

## Enemy AI

Enemies ("Stalkers") run a simple state machine: `sweep` -> `patrol` -> `engage` / `search`, with transitions based on line-of-sight checks to the player. Pathfinding is A* over a navigation grid built from each map's wall layout, with path smoothing and periodic recalculation (faster while engaging, slower while searching/patrolling).

Enemies share a basic comms system (`commsMessages`), broadcasting known player position to squadmates with a short delay, simulating radio callouts. 

AI are not omniscient and don't automatically know what the others know (calculated separately and they have to communicate).

## Audio

All sound effects (shots, etc.) are synthesized at runtime via the Web Audio API. No audio files.

## Visuals

Screen cracks/impact decals and blood drips are procedurally generated per match.