```
:I 1000 y! 1000 z! 0 r! [0 0 0 0 0] h! [0 0 0 0 0] c! `Welcome to Poker!` /N ; // Initialize game with starting chips and empty arrays for hands

:N r 1+ r! `====================` /N `ROUND ` r . /N `Your chips: ` y . ` Computer chips: ` z . /N 0 p! 0 f! 0 g! D ; // Start new round, increment round counter, reset pot and fold flags

:D `Dealing cards...` /N 5(D1) 5(D2) H ; // Deal 5 cards to each player and display hands

:D1 r /i + #F & 52 % q! q 13 / s! q 13 % 1+ q! q h /i ?! ; // Deal a card to player using pseudo-random calculation

:D2 r /i * 7 + #F & 52 % q! q 13 / s! q 13 % 1+ q! q c /i ?! ; // Deal a card to computer with different random seed

:H `Your hand:` /N 5( /i 1+ . `. ` h /i ? q! q 13 > ( q 14 = (`Ace`) /E( q 11 = (`Jack`) /E( q 12 = (`Queen`) /E( q 13 = (`King`) /E( q .))))) /E( q . ) ` of ` h /i ? 13 / t! t 0 = (`Hearts`) /E( t 1 = (`Diamonds`) /E( t 2 = (`Clubs`) /E( t 3 = (`Spades`)))) /N ) E ; // Display player's hand with card names and suits

:P `Pot: ` p . /N `Your turn. ` /N `(B)et, (C)heck, (F)old? ` /K t! t 66 = ( `How much? ` /K 48 - q! q 0 > ( q y <= ( q y - y! p q + p! `You bet ` q . /N ) /E ( `Not enough chips.` /N ) ) /E ( `Checking...` /N ) ) /E ( t 67 = ( `Checking...` /N ) /E ( t 70 = ( `You fold.` /N 1 f! z p + z! ) /E ( `Invalid choice.` /N P ))) ; // Player's turn with options to bet, check or fold

:C g 1 = ( `Computer already folded.` /N ) /E ( `Computer thinking...` /N 100() E2 q! q 1 = ( /i /j * 7 + #7 & 0 = ( `Computer folds.` /N 1 g! ) /E ( 10 #F & 1+ t! z t <= ( z t! ) z t - z! p t + p! `Computer bets ` t . /N ) ) /E ( q 2 = ( 20 #F & 1+ t! z t <= ( z t! ) z t - z! p t + p! `Computer bets ` t . /N ) /E ( 50 #F & 10 + t! z t <= ( z t! ) z t - z! p t + p! `Computer bets ` t . /N ))) ; // Computer's turn with AI based on hand strength

:E 0 q! 5( h /i ? t! /i 1+ 5 < ( /i 1+ j! 5(j 5 < ( h j ? t = ( q 1 < (1 q!) /E ( q 1 = (2 q!) ) ) j 1+ j! ))) ) q ; // Evaluate player's hand for pairs (returns 0=high card, 1=pair, 2=two pairs)

:E2 0 q! 5( c /i ? t! /i 1+ 5 < ( /i 1+ j! 5(j 5 < ( c j ? t = ( q 1 < (1 q!) /E ( q 1 = (2 q!) ) ) j 1+ j! ))) ) q ; // Evaluate computer's hand (same logic as player)

:W f 1 = ( `You folded. Computer wins pot.` /N z p + z! ) /E ( g 1 = ( `Computer folded. You win pot.` /N y p + y! ) /E ( `SHOWDOWN` /N E q! `Your hand: ` q 0 = (`High Card`) /E( q 1 = (`One Pair`) /E( q 2 = (`Two Pair`))) /N q t! E2 q! `Computer hand: ` q 0 = (`High Card`) /E( q 1 = (`One Pair`) /E( q 2 = (`Two Pair`))) /N t q > ( `You win pot!` /N y p + y! ) /E ( t q < ( `Computer wins pot!` /N z p + z! ) /E ( `Tie! Pot split.` /N p 2 / t! y t + y! z t + z! )))) ; // Determine winner based on fold flags or hand evaluation

:G I /U( N P f 0 = ( C ) W y 0 <= ( `You're out of chips. Game over!` /N /F /W ) z 0 <= ( `Computer is out of chips. You win!` /N /F /W ) `Play another round? (Y/N) ` /K t! t 89 = ( /T /W ) /E ( `Thanks for playing!` /N /F /W )) ; // Main game loop that controls entire game flow

G // Start the game by calling function G

```

