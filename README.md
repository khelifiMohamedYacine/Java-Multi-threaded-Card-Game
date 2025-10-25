# README for ECM2414 Software Development Coursework

## Overview

This document outlines the specifications and requirements for the coursework assignment for **ECM2414 - Software Development**, led by **Prof. Solomon Oyelere** for the academic year **2024/25**. The assignment focuses on developing a multi-thread card playing simulation in Java as part of a pair programming project.

### Key Details

- **Module Leader:** Prof. Solomon Oyelere
- **Academic Year:** 2024/25
- **Title:** Software Development Continuous Assessment
- **Handed Out Date:** 21st October 2024
- **Submission Deadline:** 10th December 2024


## Project Specification

### Task Description

You will implement a multi-thread card playing simulation in Java, which includes the following classes:

- `Card` Class: Represents a card with a face value.
- `CardDeck` Class: Represents a deck of cards, allowing operations to draw and discard cards.
- `Player` Class: Represents a player in the game who draws and discards cards according to game rules.
- `CardGame` Class: The main executable class that initializes the game, manages player interactions, and controls game flow.

### Game Rules

- Each player (n players) is assigned a hand of 4 cards from a 8n card pack.
- Players and decks are arranged in a ring topology.
- A player wins by having four cards of the same value in their hand.

### Game Actions

1. Players draw a card from their left deck and discard a card to their right deck.
2. The game continues until a player declares a win.

### Input/Output Requirements

- **Input Pack File:** A plain text file containing 8n non-negative integers.
- **Output Files:**
    - Each player has an individual output file (e.g., `player1_output.txt`).
    - Deck contents are saved to separate files (e.g., `deck1_output.txt`).

## Technologies

List the technologies, libraries, and frameworks used in the project. This helps other developers understand the tools involved.

- **Programming Language**: Java
- **Testing Framework**: JUnit 5
- **Build Tool**: Maven/Gradle
- **Other Libraries/Tools**: Any other major libraries (e.g., Gson, Spring Boot, etc.)


## Installation

### Prerequisites

- **Java 11** or higher
- **Maven** or **Gradle** (for dependency management)
- **JUnit 5** for running unit tests

## Running the Project

### Compile and Run:
    - Ensure Java is installed.
    - Compile the project using your IDE or command line.
    - Execute the `CardGame` class, providing the number of players and path to the input pack file.

### Running the tests

#### 1. Using Maven:
To use Maven:
1. Navigate to the root directory of the project in the terminal
2. Run the command:


    - mvn test

3. All the tests will run and the results will be displayed in the terminal

#### 2. Using an IDE:
1. Open the project in the IDE,
2. Ensure JUnit5 is added as a dependency to the project
3. Right click onto the test folder in the project or any individual test class and select **Run** or **Run All Tests**
4. The test's results will appear in the IDE's test runner window.

### Testing:
The project includes unit tests to verify the correctness of each class:

    - Card Test: Verifies card creation and manipulation.
    - CardDeck Test: Ensures deck operations (e.g., draw, discard) work correctly.
    - Player Test: Validates player actions and multi-threading behavior.
    - Game Test: Confirms the overall game flow, including win conditions.
#### 1. Card Test:
The CardTest class tests the fundamental properties of the Card class:
- `getValueTest`: Ensures the card's value is correctly set and retrieved.
- `getAgeTest and incrementAgeTest`: Validates the card’s age management by testing the increment functionality.
#### 2. CardDeck Test:
The CardDeckTest class contains tests to validate the behavior of the CardDeck class. Some of the key tests include:

- `getIndexTest`: Ensures that the deck's index is correct.
- `addCardTest`: Verifies that cards can be added to the deck and are available for polling once the deck is locked.
- `tryLockTest and unlockTest`: Ensure that the deck can be locked and unlocked appropriately, and that operations require a lock.
- `pollTest`: Ensures that cards can be polled from the deck when it is locked.
- `stopTest and nonstopTest`: Tests the logging functionality to ensure deck contents are recorded in an output file.
- `checkOwnedTest`: Validates the checkOwned method, ensuring a player cannot interact with a deck unless they "own" it (locked).
#### 3. Player Test:
The PlayerTest class focuses on the player interactions with decks and the multi-thread nature of the game. Key tests include:

- `addCardTest`: Ensures that cards are added to the player's hand correctly.
- `playTest`: Verifies that the player starts the game and can make moves.
- `playCheckWinTest`: Confirms that a player correctly wins when they have four cards of the same value.
- `playLoopTest and playLoopInterruptedTest`: Ensures that the player's action loop works as expected and handles thread interruptions correctly.
- `stopTest`: Verifies that the stop method works correctly by checking that the deck logs its contents to a file.
#### 4. CardGame Tests:
The CardGameTest class includes tests that ensure the overall game logic works correctly, including player count verification:

- `PlayerCountMismatchTest`: Ensures that an error message is shown if the number of players in the input file doesn't match the expected count.
#### 5. Utils Test:
The UtilsTest class provides tests for utility functions used throughout the project.
Test Cases:
- `getCardValues`: Verifies that card values are returned correctly as a space-separated string.
- `createOrReset`: Tests that a file can be created or reset to an empty state.

#### 6. ReflexionUtils :
The ReflectionUtils class helps access private fields and methods in other classes during testing. It’s useful for checking what’s happening inside the Player and CardDeck classes, so we can test how they work without directly changing their private members.
### Manual Testing:
A card pack file (2_win.txt) was created to test the round-robin card distribution, 
ensuring player two wins if the method works correctly. 
This confirmed the distribution was accurate. 
Larger card packs were also tested to check if the program could handle different player and deck sizes, 
as well as varying thread counts.




