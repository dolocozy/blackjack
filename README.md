# Blackjack

A console Blackjack game written in Java. Place bets with a chip wallet, hit or stand against a dealer, and play rounds until you quit or run out of chips. Built as a solo project for Sheridan College (SYST 17796).

## Features

- Betting with a chip wallet that starts at 100 chips and can never go negative
- Dealing, hit and stand turns, and bust detection
- Dealer plays by standard rules (hits below 17, stands on 17 or higher)
- Aces count as 11 or 1 automatically, depending on the hand
- Natural Blackjack (21 on the first two cards) wins immediately
- Push (tie) returns your bet
- Input validation on bets, hit/stand and play-again prompts
- Running score of rounds won, plus a session summary at the end
- The deck is rebuilt and reshuffled when it runs low

## Design

Object-oriented, with inheritance and a clear separation between game flow and the objects it uses:

| Class | Role |
|---|---|
| `Main` | Entry point |
| `Game` / `BlackjackGame` | Abstract game base class and the Blackjack session loop |
| `Player` / `BlackjackPlayer` / `Dealer` | Players, including the wallet, bet and dealer hit rule |
| `Card` / `PlayingCard` | Card abstraction and a standard playing card |
| `GroupOfCards` | Deck and hand: build, shuffle, draw, hand value with Ace logic |
| `Wallet` | Chip balance with deposit and deduct rules |

## Requirements

- Java 11 or newer (the code uses `String.isBlank()`)

## Run it

From the project folder:

```bash
mkdir -p out
javac -d out src/ca/sheridancollege/project/*.java
java -cp out ca.sheridancollege.project.Main
```

## Run the tests

The unit tests use JUnit 4 (15 tests covering hand values and Ace handling, deck building, wallet rules and dealer logic):

```bash
javac -cp out:junit-4.13.2.jar -d out test/ca/sheridancollege/project/*.java
java -cp out:junit-4.13.2.jar:hamcrest-core-1.3.jar org.junit.runner.JUnitCore ca.sheridancollege.project.BlackjackLogicTest
```

On Windows, use `;` instead of `:` in the classpath. The project can also be opened in NetBeans.

## Author

Michael Turay
