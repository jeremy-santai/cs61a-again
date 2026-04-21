# Ants Vs. SomeBees Project Summary

**Source Code:** [ants.py](../codebases/ants.py)

## Overview

A tower defense game where ants defend their colony from invading bees. Players deploy different ant types with unique abilities to stop bees from reaching the queen.

## Key Concepts Demonstrated

### Object-Oriented Programming
- **Class hierarchies** - `Insect` base class with `Ant` and `Bee` subclasses
- **Inheritance** - Specialized ants inherit from base `Ant` or `ThrowerAnt`
- **Polymorphism** - Different ant types override `action()` method
- **Composition** - `ContainerAnt` contains other ants

### Core Classes
| Class | Purpose |
|-------|---------|
| `Place` | Locations that hold insects; linked list structure |
| `Insect` | Base class with health, place, damage attributes |
| `Ant` | Defenders with food cost, deployed by player |
| `Bee` | Attackers that move toward the colony |

### Ant Types Implemented
- **HarvesterAnt** - Generates food each turn
- **ThrowerAnt** - Throws leaves at bees (with range variants: Short, Long)
- **FireAnt** - Damages all bees when it dies
- **WallAnt** - High health, blocks bees
- **HungryAnt** - Instantly kills one bee, then chews
- **ContainerAnt** - Can hold another ant (Bodyguard, Tank)
- **ScubaThrower** - Waterproof thrower
- **QueenAnt** - Doubles damage of ants behind her; game ends if she dies

### Game Mechanics
- **Water places** - Only waterproof insects survive
- **Damage doubling** - Queen buffs ants in her tunnel
- **Container logic** - Two ants can occupy same place if one is a container
