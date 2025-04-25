

```
// Poker emulator for MINT language
// Variables:
// d = deck position
// h = player hand
// c = computer hand
// p = pot
// y = player chips
// z = computer chips
// r = round number
// f = player fold flag
// g = computer fold flag
// t = temporary storage
// q = card value
// s = card suit

// Initialize game function
:I
1000 y! 1000 z! 0 r! `Welcome to Poker!` /N
;

// New round function
:N
r 1+ r! 
`====================` /N
`ROUND ` r . /N
`Your chips: ` y . ` Computer chips: ` z . /N
0 p! 0 f! 0 g! 
D // Deal cards
;

// Deal cards function
:D
`Dealing cards...` /N
5(D1) // Deal 5 cards to player
5(D2) // Deal 5 cards to computer
H // Display hands
;

// Deal a card to player
:D1
52 #F & q! // Generate random card (0-51)
q 13 / s! // Calculate suit (0-3)
q 13 % 1+ q! // Calculate value (1-13)
q h /i?! // Store in player hand array
;

// Deal a card to computer
:D2
52 #F & q! // Generate random card (0-51)
q 13 / s! // Calculate suit (0-3)
q 13 % 1+ q! // Calculate value (1-13)
q c /i?! // Store in computer hand array
;

// Display hands function
:H
`Your hand:` /N
5(
  /i 1+ . `. ` 
  h /i? s!
  s 13 > ( // Handle face cards
    s 14 = (`Ace`) /E(
    s 11 = (`Jack`) /E(
    s 12 = (`Queen`) /E(
    s 13 = (`King`) /E(
    s .)))
  ) /E(
    s .
  )
  ` of `
  h /i? 13 / t!
  t 0 = (`Hearts`) /E(
  t 1 = (`Diamonds`) /E(
  t 2 = (`Clubs`) /E(
  t 3 = (`Spades`)))
  /N
)
E // Evaluate player hand
;

// Player's turn function
:P
`Pot: ` p . /N
`Your turn. ` /N
`(B)et, (C)heck, (F)old? ` /K t!
t 66 = ( // B - Bet
  `How much? ` /K 48 - q!
  q 0 > (
    q y < (
      q y! p q + p!
      `You bet ` q . /N
    ) /E (
      `Not enough chips.` /N
    )
  ) /E (
    `Checking...` /N
  )
) /E (
t 67 = ( // C - Check
  `Checking...` /N
) /E (
t 70 = ( // F - Fold
  `You fold.` /N
  1 f!
  z p + z! // Computer gets pot
) /E (
  `Invalid choice.` /N
  P // Try again
)))
;

// Computer's turn function
:C
g 1 = ( // Already folded?
  `Computer already folded.` /N
) /E (
  `Computer thinking...` /N
  100() // Delay
  // Simple AI logic
  E2 q! // Get computer hand strength
  q 1 = ( // Has high card only
    5 #7 & 0 = ( // 30% chance to fold
      `Computer folds.` /N
      1 g!
    ) /E (
      10 #F & t! // Bet 0-10 chips
      z t < ( 
        z t! // Bet all chips if not enough
      )
      z t - z! p t + p!
      `Computer bets ` t . /N
    )
  ) /E (
  q 2 = ( // Has one pair
    20 #F & t! // Bet 0-20 chips
    z t < (
      z t! // Bet all chips if not enough
    )
    z t - z! p t + p!
    `Computer bets ` t . /N
  ) /E (
    // Has two pair or better - bet aggressively
    50 #F & 10 + t! // Bet 10-60 chips
    z t < (
      z t! // Bet all chips if not enough
    )
    z t - z! p t + p!
    `Computer bets ` t . /N
  ))
);

// Evaluate player hand - returns hand rank in q
:E
0 q! // Initialize rank to 0 (high card)
// Check for pairs
5(
  h /i? t!
  /i 1+ 5 < (
    /i 1+ /j!
    5(/j(
      h /j? t = (
        q 1 < (1 q!) /E (
        q 1 = (2 q!) // Upgrade to two pair
        )
      )
      /j 1+ /j!
    ))
  )
)
// Return rank
q
;

// Evaluate computer hand (same logic as player)
:E2
0 q! // Initialize rank to 0 (high card)
// Check for pairs
5(
  c /i? t!
  /i 1+ 5 < (
    /i 1+ /j!
    5(/j(
      c /j? t = (
        q 1 < (1 q!) /E (
        q 1 = (2 q!) // Upgrade to two pair
        )
      )
      /j 1+ /j!
    ))
  )
)
// Return rank
q
;

// Determine winner function
:W
f 1 = ( // Player folded
  `You folded. Computer wins pot.` /N
  z p + z!
) /E (
g 1 = ( // Computer folded
  `Computer folded. You win pot.` /N
  y p + y!
) /E (
  // Compare hands
  `SHOWDOWN` /N
  E q! // Get player hand rank
  `Your hand: `
  q 0 = (`High Card`) /E(
  q 1 = (`One Pair`) /E(
  q 2 = (`Two Pair`))
  /N
  q t! // Store player rank
  
  E2 q! // Get computer hand rank
  `Computer hand: `
  q 0 = (`High Card`) /E(
  q 1 = (`One Pair`) /E(
  q 2 = (`Two Pair`))
  /N
  
  // Compare ranks
  t q > ( // Player wins
    `You win pot!` /N
    y p + y!
  ) /E (
  t q < ( // Computer wins
    `Computer wins pot!` /N
    z p + z!
  ) /E (
    // Tie
    `Tie! Pot split.` /N
    p 2 / t!
    y t + y!
    z t + z!
  ))
))
; 

// Main game loop function
:G
I // Initialize
/U( // Infinite loop
  N // New round
  P // Player turn
  f 0 = ( // If player didn't fold
    C // Computer turn
  )
  W // Determine winner
  
  // Check for game over
  y 0 < (
    `You're out of chips. Game over!` /N
    /F /W // Break loop
  )
  z 0 < (
    `Computer is out of chips. You win!` /N
    /F /W // Break loop
  )
  
  // Play again?
  `Play another round? (Y/N) ` /K t!
  t 89 = ( // Y
    /T /W // Continue loop
  ) /E (
    `Thanks for playing!` /N
    /F /W // Break loop
  )
)
;

// Run game
G
```
