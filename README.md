# MINT Poker Game: User Manual

## Introduction

This manual describes a simple poker game implemented in the MINT language. The game allows a player to compete against a computer opponent in a simplified version of five-card poker.

## Getting Started

To run the poker game:
1. Enter each function (lines starting with `:` and ending with `;`) into the MINT interpreter
2. Type `T` to start the game

## Game Rules

- Each player receives 1000 chips at the start
- Each round, both players are dealt 5 cards
- The player can choose to bet, check, or fold
- The highest card in hand determines the winner
- Betting is fixed at 100 chips per round
- The game continues until one player runs out of chips

## Controls

During gameplay, you'll be prompted to make choices:
- Press `B` to bet 100 chips
- Press `C` to check (no betting)
- Press `F` to fold (surrender the hand)
- Press `Y` to play another round
- Press `N` to end the game

## Game Interface

The display shows:
- Current round number
- Your chip count and the computer's chip count
- Your hand of cards (A, 2-10, J, Q, K)
- Betting options
- Game results
- Option to play again

## Program Structure

The program consists of single-letter functions:
- `A`: Initializes the game
- `B`: Starts a new round
- `C`: Deals cards to both players
- `D` & `E`: Deal individual cards
- `F`: Displays your hand
- `G`: Gets player action
- `H`, `I`, `J`: Handle betting actions
- `K`, `L`: Evaluate hands
- `M`, `N`, `O`: Handle win/loss/tie
- `P`: End of round, check for game over
- `Q`, `R`: Game over states
- `S`: End game function
- `T`: Main function to start game

## Technical Notes

- The game uses a simple random number generator to create card values
- A card tracking system prevents duplicates
- High card only evaluation (no pairs, flushes, etc.)
- The game has minimal error checking
- Cards are represented by values 1-13 (Ace, 2-10, Jack, Queen, King)

## Limitations

- No card suits are displayed
- Only high card evaluation (no poker hand rankings)
- Fixed betting amount (100 chips)
- Computer has no strategic AI (plays automatically)
- Limited display formatting due to MINT constraints

## Tips

- Since winning is based only on high card, try to fold if you don't have face cards
- Keep track of your chip count before betting
- The game ends when either player has 0 chips

Enjoy playing MINT Poker!
