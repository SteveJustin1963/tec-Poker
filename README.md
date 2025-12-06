also see https://github.com/SteveJustin1963/tec-Poker/wiki  (muti-pages)

 

<img width="550" height="870" alt="image" src="https://github.com/user-attachments/assets/82d1089c-8caa-4010-9ab8-e5be0cc9ceb8" />




# p1 ...ugly

```
:A 1000 y! 1000 z! [0 0 0 0 0] h! [0 0 0 0 0] c! ;
:B r 1+ r! `Round:` r . /N `You:` y . `PC:` z . /N 0 p! C ;
:C 5(D) 5(E) F ;
:D r /i + #F & 13 % 1+ q! q h /i ?! ;
:E r /i * 3 + #F & 13 % 1+ q! q c /i ?! ;
:F `Hand:` 5(h /i ? . ` `) /N G ;
:G `Bet/Check/Fold? ` /K q! q 66 = H q 67 = J q 70 = I ;
:H 100 p + p! 100 y - y! `Bet 100` /N L ;
:J `Check` /N L ;
:I 1 f! `Fold` /N O ;
:K h 0 ? m! 1(h 1 ? h 2 ? h 3 ? h 4 ?) m! ;
:L c 0 ? m! 1(c 1 ? c 2 ? c 3 ? c 4 ?) n! m n > M n m > N m n = O ;
:M `You win ` p . /N y p + y! P ;
:N `PC wins ` p . /N z p + z! P ;
:O `Tie` /N p 2 / t! y t + y! z t + z! P ;
:P y 0 <= Q z 0 <= R `Again? Y/N ` /K q! q 89 = B S ;
:Q `You lose` /N S ;
:R `You win` /N S ;
:S ;
:T A B ;
T
```

```
:A 1000 y! 1000 z! [0 0 0 0 0] h! [0 0 0 0 0] c! ;
:B r 1+ r! `Round:` r . /N `You:` y . `PC:` z . /N 0 p! C ;
:C 0 i! 5(D i 1 + i!) 0 i! 5(E i 1 + i!) F ;
:D r i + #F & 13 % 1+ q! q h i?! ;
:E r i * 3 + #F & 13 % 1+ q! q c i?! ;
:F `Hand:` 5(h /i ? . ` `) /N G ;
:G `Bet/Check/Fold? ` /K q! q 66 = H q 67 = J q 70 = I ;
:H 100 p + p! 100 y - y! `Bet 100` /N L ;
:I 1 f! `Fold` /N O ;
:J `Check` /N L ;
:K h 0 ? m! 1(h 1 ? h 2 ? h 3 ? h 4 ?) m! ;
:L c 0 ? m! 1(c 1 ? c 2 ? c 3 ? c 4 ?) n! m n > M n m > N m n = O ;
:M `You win ` p . /N y p + y! P ;
:N `PC wins ` p . /N z p + z! P ;
:O `Tie` /N p 2 / t! y t + y! z t + z! P ;
:P y 0 <= (Q) /E (z 0 <= (R) /E (`Again? Y/N ` /K q! q 89 = (B) /E (S))) ;
:Q `You lose` /N S ;
:R `You win` /N S ;
:S ;
:T A B ;

```



# p2 ...bad

```
:A 1000 y! 1000 z! 0 r! 0 h1! 0 h2! 0 h3! 0 h4! 0 h5! 0 c1! 0 c2! 0 c3! 0 c4! 0 c5! ; // Initialize game
:B r 1+ r! `Round:` r . /N `You:` y . `PC:` z . /N 0 p! 0 f! 0 d! C ; // Start new round
:C D D D D D E E E E E F ; // Deal 5 cards to each player
:D d 1+ d! 53 r + d * #F & 13 % 1+ q! d 1 = (q h1!) d 2 = (q h2!) d 3 = (q h3!) d 4 = (q h4!) d 5 = (q h5!) ; // Deal card to player
:E d 1+ d! 77 r * d + #F & 13 % 1+ q! d 6 = (q c1!) d 7 = (q c2!) d 8 = (q c3!) d 9 = (q c4!) d 10 = (q c5!) ; // Deal card to computer
:F `Hand:` /N `1.` h1 ? q! q 1 = (`A`) q 11 = (`J`) q 12 = (`Q`) q 13 = (`K`) q 1 > q 10 < (q .) q! /N ; // Display card 1
:G `2.` h2 ? q! q 1 = (`A`) q 11 = (`J`) q 12 = (`Q`) q 13 = (`K`) q 1 > q 10 < (q .) q! /N H ; // Display card 2
:H `3.` h3 ? q! q 1 = (`A`) q 11 = (`J`) q 12 = (`Q`) q 13 = (`K`) q 1 > q 10 < (q .) q! /N I ; // Display card 3
:I `4.` h4 ? q! q 1 = (`A`) q 11 = (`J`) q 12 = (`Q`) q 13 = (`K`) q 1 > q 10 < (q .) q! /N J ; // Display card 4
:J `5.` h5 ? q! q 1 = (`A`) q 11 = (`J`) q 12 = (`Q`) q 13 = (`K`) q 1 > q 10 < (q .) q! /N K ; // Display card 5
:K `Bet/Check/Fold? ` /K q! q 66 = L q 67 = N q 70 = M ; // Get player action (B/C/F)
:L 100 y > (100 y!) y 100 - y! p 100 + p! `Bet 100` /N O ; // Handle bet action
:M 1 f! `Fold` /N z p + z! S ; // Handle fold action
:N `Check` /N O ; // Handle check action
:O h1 h2 > (h1 u!) h2 h1 > (h2 u!) h3 u > (h3 u!) h4 u > (h4 u!) h5 u > (h5 u!) P ; // Find player's highest card
:P c1 c2 > (c1 v!) c2 c1 > (c2 v!) c3 v > (c3 v!) c4 v > (c4 v!) c5 v > (c5 v!) f 1 = (S) u v > Q v u > R u v = T ; // Find PC's highest card
:Q `You win ` p . /N y p + y! S ; // Player wins
:R `PC wins ` p . /N z p + z! S ; // Computer wins
:T `Tie` /N p 2 / t! y t + y! z t + z! S ; // Handle tie
:S y 0 <= (U) z 0 <= (V) `Again? Y/N ` /K q! q 89 = (B) W ; // Check game over
:U `You lose` /N W ; // Game over - player loses
:V `You win!` /N W ; // Game over - player wins
:W ; // Empty function to end game
:X A B ; // Main function
X // Run the game
```



# p3 good

```
:S 12345 s ! ;
:C s 7 * 3 + s ! s 32555 > ( 1 s ! ) s 13 / ' /r 1 + ;
:I [ 0 0 0 0 0 ] h ! [ 0 0 0 0 0 ] c ! ;
:D 5 ( C h /i ?! C c /i ?! ) ;
:P " 10 < ( 48 + /C 32 /C ) /E ( " 10 = ( ' 84 /C 32 /C ) /E ( " 11 = ( ' 74 /C 32 /C ) /E ( " 12 = ( ' 81 /C 32 /C ) /E ( ' 75 /C 32 /C )))) ;
:T 1000 y ! 1000 z ! 200 p ! `CPU:    [ X X X X X ]    Bank:$` z . /N /N `          POT:$` p . /N /N `YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P ` ]    Bank:$` y . /N ;
:V `CPU:[` 5 ( c /i ? P ) ` ]` /N `YOU:[` 5 ( h /i ? P ) ` ]` /N ;
:G S I D T ;
```



```
:S 12345 s ! ;
//:C s 7 * 3 + s ! s 32555 > ( 1 s ! ) s 13 / ' /r 1 + ;
  :C s 75 * 74 + 32749 /r s ! s 13 / ' /r 1 +  ;
:I [ 0 0 0 0 0 ] h ! [ 0 0 0 0 0 ] c ! ;
:D 5 ( C h /i ?! C c /i ?! ) ;
:P " 10 < ( 48 + /C 32 /C ) /E ( " 10 = ( ' 84 /C 32 /C ) /E ( " 11 = ( ' 74 /C 32 /C ) /E ( " 12 = ( ' 81 /C 32 /C ) /E ( ' 75 /C 32 /C )))) ;
:T 1000 y ! 1000 z ! 200 p ! `CPU:    [ X X X X X ]    Bank:$` z . /N /N `          POT:$` p . /N /N `YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P ` ]    Bank:$` y . /N ;
:V `CPU:[` 5 ( c /i ? P ) ` ]` /N `YOU:[` 5 ( h /i ? P ) ` ]` /N ;
:G I D T ;

> S    // Initialize seed ONCE
> G    // Game 1: YOU: [ 5 2 9 1 2 ]
> G    // Game 2: YOU: [ 8 3 K 7 4 ] (different!)
> G    // Game 3: YOU: [ J 9 5 2 Q ] (different!)
```

```
:C s 75 * 74 + 32749 / /r s ! s 13 / ' /r 1 + ;
:D 5 ( C h /i ?! C c /i ?! ) ;
:G I D T ;
:I [ 0 0 0 0 0 ] h ! [ 0 0 0 0 0 ] c ! ;
:P " 10 < ( 48 + /C 32 /C ) /E ( " 10 = ( ' 84 /C 32 /C ) /E ( " 11 = ( ' 74 /C 32 /C ) /E ( " 12 = ( ' 81 /C 32 /C ) /E ( ' 75 /C 32 /C ) ) ) ) ;
:S 12345 s ! ;
:T 1000 y ! 1000 z ! 200 p ! `CPU:    [ X X X X X ]    Bank:$` z . /N /N `          POT:$` p . /N /N `YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P ` ]    Bank:$` y . /N ;
:V `CPU:[` 5 ( c /i ? P ) ` ]` /N `YOU:[` 5 ( h /i ? P ) ` ]` /N ;
```


```

:C s 75 * 74 + 32749 / /r s ! s 13 / ' /r 1 + ;
:D 5 ( C h /i ?! C c /i ?! ) ;
:G I D T ;
:I [ 0 0 0 0 0 ] h ! [ 0 0 0 0 0 ] c ! ;
:P " 10 < ( 48 + /C 32 /C ) /E ( " 10 = ( ' 84 /C 32 /C ) /E ( " 11 = ( ' 74 /C 32 /C ) /E ( " 12 = ( ' 81 /C 32 /C ) /E ( ' 75 /C 32 /C ) ) ) ) ;
:S 12345 s ! ;

:T
1000 y ! 1000 z ! 200 p !
`CPU:    [ ` c 0 ? P c 1 ? P c 2 ? P c 3 ? P c 4 ? P `] Bank:$` z . /N/N
`          POT:$` p . /N/N
`YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P `] Bank:$` y . /N
;
:V `CPU:[` 5 ( c /i ? P ) ` ]` /N `YOU:[` 5 ( h /i ? P ) ` ]` /N ;
```

Perfect — that’s a very clear and solid design choice. 🎯

So we’ll assume:

> You have an infinite virtual deck with card values 1–13, each representing a **rank only** (Ace → King), and you can draw as many times as you want with duplicates allowed.

That means:

* No suits.
* Duplicates are allowed (two Kings in the same hand are fine).
* Random draws are independent.
* All logic operates only on rank values 1–13.

---

### ✅ What this simplifies

| Feature           | Result                                                       |
| ----------------- | ------------------------------------------------------------ |
| **Dealing logic** | Just call `C` repeatedly; no need to track used cards.       |
| **Memory use**    | Two 5-element arrays (`h` and `c`).                          |
| **Display logic** | `:P` already converts 1–13 → “1,2,…,10,T,J,Q,K”.             |
| **Randomness**    | Your fixed RNG now handles it fine.                          |
| **Future logic**  | You can implement hand ranking easily using 1–13 arithmetic. |

---

### 🎮 The core game state now

```mint
:S 12345 s ! ;                               // Seed RNG
:C s 75 * 74 + 32749 / /r s ! s 13 / ' /r 1 + ; // Random 1–13
:I [0 0 0 0 0] h ! [0 0 0 0 0] c ! ;         // Init hands
:D 5 ( C h /i ?!  C c /i ?! ) ;              // Deal hands
:T 1000 y ! 1000 z ! 200 p !                  // Setup & print table
   `CPU:    [ X X X X X ]    Bank:$` z . /N/N
   `          POT:$` p . /N/N
   `YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P `] Bank:$` y . /N ;
:V `CPU:[` 5 ( c /i ? P ) `]` /N `YOU:[` 5 ( h /i ? P ) `]` /N ;
:G I D T ;                                   // Game start
```

Then just run:

```
G
```

and you’ll get a new hand each time.
Each card value (1–13) is drawn independently — “infinite supply” model.

---

### 🔹 Next logical step

Now that dealing works perfectly, the next interesting feature would be **hand evaluation** — e.g. detect pairs, three-of-a-kind, or straights.

Would you like me to add a small **MINT function to evaluate a 5-card hand (1–13)** so it prints something like
`"PAIR"` / `"THREE KIND"` / `"STRAIGHT"` / `"HIGH CARD"`?

Good thinking — yes, and that’s *exactly* the next logical step if you want the CPU’s hand to be displayed (and later evaluated) the same way as the player’s.

---

### 🔹 Right now

Your display line for **YOU** is:

```mint
`YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P `] Bank:$` y . /N
```

That means:

* Fetch each element of the **player hand array `h`**
* Pass it through `:P` to print as a card rank symbol (1–13 → 1,T,J,Q,K)
* Then print the player’s bank `$y`

---

### 🔹 For the CPU

You can make a mirror version that does the same thing for `c` (the CPU hand array):

```mint
`CPU:    [ ` c 0 ? P c 1 ? P c 2 ? P c 3 ? P c 4 ? P `] Bank:$` z . /N
```

Now both hands will display properly.

---

### 🔹 Example combined display section

So, update your `:T` function to this:

```mint
:T
1000 y ! 1000 z ! 200 p !
`CPU:    [ ` c 0 ? P c 1 ? P c 2 ? P c 3 ? P c 4 ? P `] Bank:$` z . /N/N
`          POT:$` p . /N/N
`YOU:    [ ` h 0 ? P h 1 ? P h 2 ? P h 3 ? P h 4 ? P `] Bank:$` y . /N
;
```

That gives both CPU and player cards visibly — no more `[X X X X X]`.

---

### 🔹 Or, if you still want to hide CPU cards initially

Keep the current line with `[ X X X X X ]` in `:T`, and then make the **`:V` function** show the real cards:

```mint
:V
`CPU:[` 5 ( c /i ? P ) `]` /N
`YOU:[` 5 ( h /i ? P ) `]` /N
;
```

That way:

* `T` = table view (CPU cards hidden)
* `V` = reveal both hands after play

---

✅ **Summary:**

| Mode        | Description                                  | Code          |
| ----------- | -------------------------------------------- | ------------- |
| Show both   | Copy the `h` printing pattern to `c`         | use in `:T`   |
| Hide/reveal | Keep `X X X X X` in `:T`, show cards in `:V` | current style |

---

Would you like me to show a version that automatically calls `:V` *after* a keypress — so it mimics the “reveal” moment after you hit Enter?

Excellent — you’ve now reached a really solid milestone. 🃏
At this point your MINT poker engine has:

✅ Random generator (`:C`)
✅ Deck model (1–13 infinite ranks)
✅ Array-based hands for YOU + CPU (`h`, `c`)
✅ Dealing (`:D`)
✅ Display + reveal (`:T`, `:V`)
✅ Persistent banks and pot

That means you’ve got the “dealing loop” working exactly like a minimal casino draw-poker engine.
Now you can evolve the game in two major layers:

---

## 🎯 **1️⃣ Hand Evaluation**

Give meaning to the five cards each player has.

Start simple:

| Hand Type           | Rule                   |
| ------------------- | ---------------------- |
| **Pair**            | Any two equal ranks    |
| **Two Pair**        | Two distinct pairs     |
| **Three-of-a-Kind** | Three equal ranks      |
| **Straight**        | Five consecutive ranks |
| **Four-of-a-Kind**  | Four equal ranks       |
| **High Card**       | Anything else          |

So you’d write a function like:

```mint
:H h /S ( h /i ? ... ) ;    // scan your array and count matches
```

You can store counts in a `[13]` frequency array, then test patterns.

👉 This lets you compare YOU vs CPU and decide who wins the pot.

---

## 💰 **2️⃣ Betting & Bank Logic**

Now that the table and pot are defined:

* Subtract bets from `y` (you) and `z` (CPU).
* Add them into `p` (pot).
* After evaluation, award the pot to the winner.

Example structure:

```mint
:B 50 y - y! 50 z - z! 100 p + p! ;
:W y p + y! 0 p ! ;     // give pot to player
:L z p + z! 0 p ! ;     // give pot to cpu
```     

Then `:G` could become:

```
:G I D T B H ... V ;
```

---

## 🤖 **3️⃣ Basic CPU “AI”**

Later, after evaluation works:

* You can have CPU decide to **fold**, **call**, or **raise** based on random chance or hand strength.

Example:

```mint
:CJ C 5 < (`CPU folds`) /E (`CPU calls`) ;
```

---

## 🧠 **4️⃣ Gameplay Loop**

Make `:G` a full round:

```
:G
I D T          // init + deal + show table
B              // both players bet
H              // evaluate hands
V              // reveal cards
W or L         // distribute pot
;
```

Then you can loop:

```
/U(G)
```

for infinite rounds until someone’s bank = 0.

---

## ✨ **5️⃣ Optional Enhancements**

* Keep statistics of wins/losses.
* Animate “dealing” by printing one card at a time.
* Add keypress pauses between stages (`/K` waits for Enter).
* Add text like: `You win!`, `CPU wins!`, `Draw!`.

---

### ✅ Recommended next immediate step

Start with **Hand Evaluation** (`:H`) —
because once you can *score a hand*, everything else (betting, AI, pot handling) makes sense.

---

Would you like me to sketch a **MINT-compatible hand-ranking function** that counts ranks (pairs, triples, etc.) so you can plug it straight into your existing system?

---

## Game Type

This is **5-Card Stud Poker** in **heads-up** format (1v1: You vs CPU).
