# Hog Dice Game Project Summary

**Source Code:** [hog.py](../codebases/hog.py)

## Overview

A two-player dice game where players choose how many dice to roll each turn. First to reach 100 points wins. Features special rules like "Pig Out" and "Sus Fuss."

## Key Concepts Demonstrated

### Control Flow & Game Logic
- **Turn-based simulation** - `play()` function alternates between players
- **Strategy functions** - Higher-order functions that decide dice count
- **Update functions** - Calculate new scores with rule variations

### Higher-Order Functions
- **`always_roll(n)`** - Returns a strategy that always rolls n dice
- **`make_averaged(fn, samples)`** - Returns function that averages fn over samples
- **Strategy functions** - Take (score, opponent_score), return num_rolls

### Special Rules

| Rule | Description |
|------|-------------|
| **Pig Out** | Rolling a 1 on any die scores only 1 point total |
| **Boar Brawl** | Rolling 0 dice scores 3 × abs(ones digit - tens digit of opponent) |
| **Sus Fuss** | Scores with 3 or 4 factors round up to next prime |

## Core Functions

| Function | Purpose |
|----------|---------|
| `roll_dice(num_rolls, dice)` | Simulate rolling dice, return sum (or 1 if any 1s) |
| `boar_brawl(player, opponent)` | Calculate points for rolling 0 dice |
| `take_turn()` | Execute one turn, apply rules |
| `sus_update()` | Update score with Sus Fuss rule |
| `play()` | Simulate full game between two strategies |

## Strategy Development
- **`boar_strategy`** - Roll 0 if Boar Brawl gives ≥ threshold points
- **`sus_strategy`** - Roll 0 if Sus Fuss would boost score significantly
- **`make_averaged`** - Used to find optimal dice count experimentally
