# Game Project Scope Study

## Required Readings

-   [Game Project](https://github.com/ga-wdi-boston/game-project)
-   [Game API](https://github.com/ga-wdi-boston/game-project-api)
-   [What is a User Story](https://www.mountaingoatsoftware.com/agile/user-stories)

## Deliverables

After reading the `game-project` prompt and the `game-project-api` documentation
please do the following and be prepared to share and discuss during our next
class.

Submit detailed answers to the following in this file via a pull request:

-   A wireframe of what your game project will look like.
-   The data structure you plan to use.
-   How you will take the markup of the game board and represent it in JS
-   How you plan to approach this project.
-   4-8 user stories for your game project.
-   How you plan to keep your code modular.
-   What creative spin will you add to your project?
-   How will you use version control to backup / track your project?
-   Do you plan to attempt any of the bonuses?

You may want to submit pictures for your wireframes and/or user stories.
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
has instructions to link to a picture you've uploaded to a service like [Imgur](http://imgur.com/).

# Game Project Scope

## Table of Contents
- [Project Approach](#project-approach)
- [Modularity](#modularity)
- [Version Control](#version-control)
- [Creative Spin](#creative-spin)
- [Application View Template](#application-template-and-view-states)
  - [Header View States](#header-view-states)
  - [Content View States](#content-view-states)
- [User Stories & Wireframes](#user-stories-and-wireframes)
  - [Public View](#1-public-view)
  - [Sign Up](#2-sign-up)
  - [Sign In](#3-sign-in)
  - [Change Password](#4-change-password)
  - [Start New Game](#5-start-new-game)
  - [Play Game](#6-play-game)
  - [Game Over](#7-game-over)
  - [Backlog](#backlog)
- [Data Structures and Object Definitions](#data-structures-and-object-definitions)
  - [Board Object](#board-object)
  - [Cue Object](#cue-object)
  - [Square Object](#square-object)
- [Planned Bonuses](#planned-bonuses)


## Project Approach

The approach to this project is to leverage view states to keep the level of complexity of the game application to a minimum. The game display will be structured as four layout components that will manage their own content based on which view the application is expecting. These view states will be determined by the user's authentication status, the current state of game play, and any user input. Ideally, this structure will result in simple system of components that communicate state changes to each other but who are responsible for managing their own logic and display output.

## Modularity

The overall approach of using componentized view states at the UI level will map back to the program logic and code structure. The HTML for the view states described below will be created by the application and switched in and out of the DOM using jQuery as view states are required to change. The code to handle these updates will be included as methods in JavaScript libraries that correspond the UI view states.

Additionally, the code for handling view updates, API calls, event handlers, and game functionality, will be stored in separate JavaScript libraries to allow for greater flexibility and code portability.

## Version Control

Each feature that will be created should map back to one of the existing user stories. Each of these user stories will have a new branch created. Once a feature is complete and has been tested, the feature branch will be merged back into the release branch and the next feature branch will be created.

While development work on a feature branch is in progress, code will be committed on a regular basis as individual pieces of functionality are completed. These commits will include well-structured commit messages with clear, scannable titles and detailed bodies containing explainations of what was done and why.

## Creative Spin

This project is going to present an minimalist design philosophy, both on the aesthetic and architectural side. It will attempt to demonstrate creativity by leveraging, as much as possible, the capabilities available in the data and frameworks used in the application.

## Application Template and View States
The game application uses this template structure to define its content view states to update them as views change.

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/01-template.png" target="_blank"><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/01-template.png" width="50%"></a>

The template consists of four elements:
- **Header:** conent depends on authentication state of the user
- **Content:** fixed size area for showing game play and dialog boxes for user input
- **Message:** element for showing game messages to the player(s)
- **Footer:** static footer containing copyright information


### Header View States
The header has two view states, _public_ or _private,_ depending on whether the user has been authenticated.


#### Public Header View State
* _**Link:**_ sign up
* _**Link:**_ sign in


#### Private Header View State
* _**Brand Title:**_ "tic tac toe”
* _**Menu:**_ User (email) Dropdown
    * _**Link:**_ save game (only active in live game)
    * _**Link:**_ load game
    * _**Link:**_ change password
    * _**Link:**_ sign out


### Content View States
The main square in application display can contain
- _**Grid:**_ displays a 3x3 grid for game play views or to look like the game board for static views
- _**Form:**_ displays a box the size of the 3x3 grid containing form inputs


#### Content View State: Splash Screen
* _**Layout:**_ 3x3 board grid
* _**Content:**_ Characters for “tic tac toe” in grid


#### Content View State: Sign up
* _**Layout:**_ form
* _**Inputs:**_ email, password, and confirm password
* _**Links:**_ submit and cancel


#### Content View State: Sign in
* _**Layout:**_ : form
* _**Inputs:**_ email and password
* _**Links:**_ submit and cancel


#### Content View State: Change Password
* _**Layout:**_ form
* _**Inputs:**_ password and confirm password
* _**Links:**_ submit and cancel


#### Content View State: Start Game
* _**Layout:**_ 3x3 board grid
* _**Links:**_ start game


#### Content View State: Play Game
* _**Layout:**_ 3x3 board grid
* _**Squares:**_
    * _**Link:**_ clickable square as blank button before select
    * _**Output:**_ static display of “X” or “O” after select


#### Content View State: Game Over
* _**Layout:**_ 3x3 board grid
* Link: play again


## User Stories and Wireframes

### 1. Public View
As a unauthenticated user, I want to access a public view so that I can create an account or sign in.
- **User:** unauthenticated
- **View:** Public
- **Header View State:** Public
- **Content View State:** Splash Screen
- **Message:** inactive
- **Footer:** static
- **activeGame:** false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/02-public-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/02-public-view.png" width="50%"></a>

### 2. Sign Up
As a new user, I want to be able to create an account so that I can sign in and play the game.
- **User:** unauthenticated
- **View:** Sign up
- **Header View State:** Public with “sign up” active
- **Content View State:** Sign up
- **Message:** inactive
- **Footer:** static
- **activeGame:** false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/03-sign-up-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/03-sign-up-view.png" width="50%"></a>

### 3. Sign In
As an existing user, I want to be able to sign in so that I can play the game.
- **User:** unauthenticated
- **View:** Sign In
- **Header View State:** Public with “sign in” active
- **Content View State:** Sign In
- **Message:** display success/error messages
- **Footer:** static
- **activeGame:** false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/04-sign-in-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/04-sign-in-view.png" width="50%"></a>

### 4. Change Password
As an authenticated user, I want to change my password so that I can keep my account secure.
- **User:** unauthenticated
- **View:** Change Password
- **Header View State:** Private
- **Content View State:** Change Password
- **Message:** display success/error messages
- **Footer:** static
- **activeGame:** true or false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/05-change-password-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/05-change-password-view.png" width="50%"></a>

### 5. Start New Game
As an authenticated user, I want to start a new game so that I can begin playing.
- **User:** authenticated
- **View:** Start Game
- **Header View State:** Private
- **Content View State:** Start Game
- **Message:** inactive
- **Footer:** static
- **activeGame:** false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/06-start-game-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/06-start-game-view.png" width="50%"></a>

### 6. Play Game
As player, I want to make a move so the game can determine if that move changes the outcome of the game (active, win, lose, tie, draw).
- **User:** authenticated
- **View:** Play Game
- **Header View State:** Private
- **Content View State:** Play Game
- **Message:** display game play messages
- **Footer:** static
- **activeGame:** true

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/07-play-game-vIew.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/07-play-game-vIew.png" width="50%"></a>


### 7. Game Over
As a player, I want to see when the game is over so that I can learn who won and choose to play again.
- **User:** authenticated
- **View:** Game Over
- **Header View State:** Private
- **Content View State:** Game Over
- **Message:** display game status messages
- **Footer:** static
- **activeGame:** false

<a href="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/08-game-over-view.png" target="_blank" ><img src="https://s3.amazonaws.com/pliddy-ga/tic-tac-toe/wireframes/08-game-over-view.png" width="50%"></a>

### Backlog
These user stories have not yet been groomed and do not have updated wireframes:
-  **Save Game:** As a player, I want to be able to save my current game so that I can continue playing later.
-  **Load Game:** As a returning player, I want to be able to load one of my saved games so that i can continue playing.
-  **Total Score:** As a player, I want to see the total number of games I have won so that I can understand my skill level.


## Data Structures and Object Definitions
The following data structures define how the game will handle the `board`, `squares` on the board, and data structures called `cues` that monitor three squares in a row and determine f the status of the game as a result of the values of those squares.

### Board Object
A **Board** object is the primary data structure representing the game play environment.

#### Attributes
* _**squares[ ]:**_ an array of nine Square object representing the game board
* _**cues[ ]:**_ an array of eight Cue objects representing 3 rows, 3 columns, and 2 diagonals

#### Methods
* _**select( ):**_ the game updates itself when a selection is made
* _**draw( ):**_ the game updates its view and its squares to display the current game state
* _**checkWin( ):**_ the game checks to see if the last move has resulted in a win for that player
* _**reset( ):**_ resets the game back to default (ready to play new game)


### Cue Object
A **Cue** object represents a structure consisting of three sequential squares of the game board. If all three square values are identical, a player has won the game.

#### Attributes
* _**id:**_ astring identifying cue [ ‘row1', ‘row2', ‘row3', ‘col1', ‘col2', ‘col3', ‘dia1', ‘dia2’ ]
* _**squares[ ]:**_ an array of three Square objects

#### Methods
* _**checkWin( ):**_ compares the values in all three squares; returns:
    * 1 if all values are 'X’
    * -1 if all values are 'O’,
    * 0 if all values are not “X” or “O"

### Square Object
A **Square** object represents one of the squares on the game board.

#### Attributes
* _**cell:**_ which cell number is represented by this square (0-9)
* _**value:**_ null (default) | 'X' | ‘O’

#### Methods
* _**select( ):**_ the square sets its value to “X” or “O"
* _**draw( ):**_ the square updates its display to “X” or “O” and disables click input for future turns
* _**reset( ):**_ resets the square back to default (ready to play new game)

## Planned Bonuses

Once the basic requirements of the game project are complete, I plan to:
- Improve the overall visual experience of the game by leveraging Bootstrap for its out-of-the-box styling and interactivity and experiment with CSS animations to give the game smooth transitions between view state updates.
- Allow two players to play against each other from different devices
- Allow for a live player to play against the computer without requiring a complex rules engine
