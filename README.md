

# Poker Hand Victor

This is a C++ application that analyzes poker hands using the SFML (Simple and Fast Multimedia Library) library for graphical output. The program allows users to input their hand and the community cards (flop, turn, and river) to determine which hands might beat theirs at different stages of a Texas Hold'em game. It visualizes the user's hand on a window and prints the analysis to the console.

## Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [How It Works](#how-it-works)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features
- **Hand Input**: Allows users to input their two private cards and the five community cards (flop, turn, river).
- **Hand Analysis**: Determines the rank of the user's hand (e.g., High Card, Flush, Straight Flush) and identifies hands that beat it based on the current community cards.
- **Graphical Visualization**: Displays the user's hand using SFML, rendering cards as white rectangles with values and suits.
- **Stage-by-Stage Analysis**: Evaluates potential winning hands after the flop, turn, and river.
- **Error Handling**: Includes basic checks for font loading and input processing.

## Prerequisites
Before running this application, ensure you have the following installed on your system:
- **C++ Compiler**: A compatible C++ compiler (e.g., g++ for GCC).
- **SFML Library**: Version 2.x of the Simple and Fast Multimedia Library.
  - On Ubuntu/Debian: `sudo apt-get install libsfml-dev`
  - On macOS (with Homebrew): `brew install sfml`
  - On Windows: Download from [SFML Official Site](https://www.sfml-dev.org/download.php) and set up manually.
- **Font File**: The code assumes an "arial.ttf" font file is present in the project directory. You can download Arial or use another TTF font and rename it accordingly.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd poker-hands-analyzer
   ```

2. **Install SFML**:
   Follow the instructions for your operating system as listed in the [Prerequisites](#prerequisites) section to install SFML.

3. **Obtain a Font File**:
   - Place an "arial.ttf" file in the project directory. You can download Arial from a trusted source or use another TTF font (e.g., from Google Fonts) and rename it to "arial.ttf".

4. **Compile the Code**:
   Use a C++ compiler with SFML linked. Example command using g++:
   ```bash
   g++ -o poker_hands main.cpp -lsfml-graphics -lsfml-window -lsfml-system
   ```
   - Replace `main.cpp` with the name of your source file if different.
   - Ensure the SFML library paths are correctly set in your compiler flags if installed in a non-standard location.

5. **Run the Application**:
   ```bash
   ./poker_hands
   ```
   (On Windows, use `poker_hands.exe` if applicable.)

## Usage
1. **Start the Program**:
   Run the compiled executable as described above. A window titled "Poker Hands" will open.

2. **Input Your Hand**:
   - Enter the value and suit of your first card (e.g., `10 S` for 10 of Spades).
     - Values: 2-13 (where 11 = Jack, 12 = Queen, 13 = King, 14 = Ace; 1 is also accepted as Ace).
     - Suits: `S` (Spades), `H` (Hearts), `D` (Diamonds), `C` (Clubs).
   - Enter the value and suit of your second card in the same format.

3. **Input Community Cards**:
   - Enter the three flop cards one by one when prompted.
   - Enter the turn card when prompted.
   - Enter the river card when prompted.
   - Use the same value and suit format as above.

4. **View Results**:
   - The console will display hands that beat your hand after each stage (flop, turn, river).
   - The SFML window will visually show your two cards.

5. **Close the Application**:
   - Click the window's close button (X) to exit.

## Code Structure
- **Main Function**: Handles the SFML window setup, user input, and game loop.
- **Card Structure**: Defines a `Card` with `value` (2-14) and `suit` (S, H, D, C).
- **Rank Enumeration**: Lists poker hand ranks (High Card to Royal Flush).
- **Helper Functions**:
  - `compareCards`: Sorts cards by value.
  - `isFlush`: Checks if all cards have the same suit.
  - `isStraight`: Checks if cards form a consecutive sequence.
  - `determineRank`: Determines the poker rank of a hand.
  - `generateHands`: Generates all possible two-card hands from the table and deck that beat the user's hand.
  - `printCardSFML`: Renders a single card graphically using SFML.
  - `printHandsSFML`: Renders multiple hands (currently set to display the user's hand).

## How It Works
1. **Input Processing**:
   - The program reads user input for two private cards and five community cards, converting Ace (1 or 14) to 14 for consistency.
2. **Hand Evaluation**:
   - The `determineRank` function checks for flushes and straights, assigning a rank. Currently, it only supports basic rankings (e.g., High Card, Flush, Straight, Straight Flush, Royal Flush).
   - The `generateHands` function compares the user's hand rank against all possible two-card combinations from the table and remaining deck, identifying winning hands.
3. **Graphical Output**:
   - `printCardSFML` draws each card as a white rectangle with the value in the top-left and suit in the bottom-right.
   - The user's hand is displayed at coordinates (50, 200) and (130, 200).
4. **Stage Progression**:
   - After each input (flop, turn, river), the program updates the table cards and re-evaluates beating hands.

## Limitations
- **Partial Rank Detection**: Only detects High Card, Flush, Straight, Straight Flush, and Royal Flush. Other ranks (e.g., Pair, Full House) are not implemented.
- **Graphical Limitation**: Only displays the user's hand; beating hands are listed in the console, not graphically.
- **Font Dependency**: Requires "arial.ttf" in the directory; failure to load causes rendering issues.
- **Input Validation**: Limited error handling for invalid inputs (e.g., wrong suit characters).
- **Performance**: Generating hands for a full deck could be optimized with a more efficient algorithm for larger card sets.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -m "Add new feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request with a description of your changes.

Please ensure your code follows C++ best practices and includes comments where necessary.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For questions or support, please contact [Your Name] at [your.email@example.com] or open an issue on the repository.

---

### Notes for You
- **Customization**: Adjust the contact information, repository URL, and license file as needed.
- **Enhancement Suggestions**: If you plan to expand this, consider adding:
  - Full poker rank detection (e.g., Pair, Two Pair).
  - Graphical display of beating hands.
  - Input validation with error messages.
  - A deck shuffle to simulate random community cards.
- **Font Issue**: If "arial.ttf" isn’t available, download a TTF font, place it in the project directory, and update the file name in `printCardSFML` if necessary.

