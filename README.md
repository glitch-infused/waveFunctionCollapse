# Wave function collapse

An algorithm for generating a 2D array of tiles based on the concept of wave function collapse (also called reduction of the state vector) from quantum mechanics.

## A simplified explanation

This is my modified version of WFC.

Wave function collapse works trough having a collection of tiles, and some rules on how these tiles connect and can get placed on a grid.

The algorithm starts by initialising a grid where every element of the grid is in a superposition of being every tiles at once. Then the following steps get repeated:

### 1) Finding the cell with the lowest entropy

Entropy in this context is used as a measure to the amount of possible options for a cell. Specifically Entropy is the amount of 'binary' choices that can be made to decide the value of that cell, or the log_2 of the amount of possible values.

The algorithm finds a cell with the lowest entropy, that isn't zero since we have already assigned these cells a tile. Since it is possible for multiple cells to have the same amount of entropy, the algorithm pick one of these cells at random.

### 2) Collapseing that cell

When we find the cell with the lowest entropy we observe the cell resulting in it collapseing to the tile that the cell is most likely to be. In my implementation every tile has the same probability, so we just pick one of the possible tiles, and set the cell's entropy to zero.

### 3) Propagating the collapse

Once the cell has been collapsed to a tile, this modifies to possible values for the neighbouring tiles. This results in new entropy values, and tends to decrease the entropy of neighbouring tiles. At a certain point all of the entropy values are zero, which means all of the cells are assigned a single tile.

!!! This doesn't always happen for tiles with stricter rules, in my case this works because there is a tile that fits any situation of neighbouring tiles.

## Possible further experiments

- combining WFC with backtracking for problems that don't guarantee a solution
- converting this program into a library and making more accessible interfaces for designing rules
- WFC in higher (or lower :]) dimensions
