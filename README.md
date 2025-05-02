# Word Search Program

## Overview
This program searches for specified words hidden within a matrix of letters. It can detect words placed horizontally, vertically, and diagonally in any direction. When a word is found, the program reports its location and direction and generates a colorized PPM image highlighting the found words.

## Features
- Reads a word search matrix and a list of words from a file
- Searches for words in 8 directions (N, NE, E, SE, S, SW, W, NW)
- Reports the starting position and direction of each found word
- Lists any words that could not be found in the matrix
- Generates a PPM image file with found words highlighted in different colors based on word length:
  - Words ≤ 5 letters: Red
  - Words ≤ 10 letters: Green
  - Words > 10 letters: Blue

## How to Use

### Input File Format
The program expects an input file with the following format:
1. Row and column dimensions (two integers)
2. The word search matrix (characters with no spaces)
3. List of words to find (one per line)

Comments can be included in the file by starting a line with `#`.

### Running the Program
1. Compile the program:
   ```
   g++ -o wordsearch Dynamic-Word-Search-Solver.cpp
   ```
2. Run the compiled program:
   ```
   ./wordsearch
   ```
3. When prompted, enter the name of the input file.
4. The program will display:
   - The matrix from the input file
   - Each found word with its position and direction
   - A list of words that could not be found

### Output
- Console output showing found words with positions and directions
- A file named `word_search_results.ppm` containing a colorized image of the word search

## Technical Details

### Algorithm
The program searches for each word by:
1. Checking every position in the matrix as a potential starting point
2. Looking in all 8 directions from each position
3. Comparing characters along each direction with the target word
4. Recording successful matches with position and direction information

### Data Structures
- 2D array to store the word search matrix
- 1D arrays to store the word bank (with and without spaces)
- 3D array to track the positions of letters in found words for PPM generation
- Vector to store words that were not found

### File Handling
- Input: Reads word search puzzles from text files
- Output: Generates PPM image files showing found words

## Example
For a word search containing movie titles, the program might output:
```
The file opened is: movies.txt
Number of rows: 15 Number of columns: 15

HGODFATHER...
TITANIC......
...

found GODFATHER at (1,2): (Direction = E)
found TITANIC at (2,1): (Direction = E)
...

Couldn't find these movies:
AVATAR
...
```

## Notes
- Words in the search matrix and word bank are converted to uppercase for matching.
- Words can have spaces in the word bank, but spaces are removed when searching.
- The program generates a PPM file, which is a simple image format that can be opened with most image viewers.
