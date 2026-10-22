# Representation of a Real-World Problem as a Markov Decision Process

## Aim

To represent a real-world problem using a Markov Decision Process (MDP) by defining states, actions, transition probabilities, and rewards.

---

## Problem Statement

### Problem Description

**Robot Navigation in a Grid**

A robot moves inside a 3 × 3 grid to reach a destination. It can move up, down, left, or right. The robot receives a positive reward for reaching the goal and a negative reward for hitting an obstacle. The objective is to find the best path to reach the destination.

---

## MDP Components

A Markov Decision Process is represented as:

\[
MDP = (S, A, P, R, \gamma)
\]

| Symbol | Meaning |
|---|---|
| `S` | Set of states |
| `A` | Set of actions |
| `P` | Transition probability function |
| `R` | Reward function |
| `γ` | Discount factor (0.9) |

---

## State Space

The robot operates in a 3 × 3 grid, where each cell represents a state.

```text
S = {
    (0,0), (0,1), (0,2),
    (1,0), (1,1), (1,2),
    (2,0), (2,1), (2,2)
}
```

- **Start state:** `(0,0)`
- **Goal state:** `(2,2)`
- **Obstacle:** `(1,1)`

---

## Sample State

`(0,0)` — The robot is at the top-left corner of the grid.

---

## Action Space

```text
A = {
    Up,
    Down,
    Left,
    Right
}
```

---

## Sample Action

`Right` — The robot moves one cell to the right from `(0,0)` to `(0,1)`.

---

## Transition Probability

The transition probability describes the probability of reaching the next state after performing an action.

- Probability of moving in the intended direction: `0.8`
- Probability of moving in another direction: `0.2`
- If movement reaches a boundary or obstacle, the robot stays in the same state.
- The goal state is `(2,2)`.

For example:

\[
P((0,1)\mid(0,0),Right)=0.8
\]

---

## Reward Function

The robot receives rewards as follows:

| Situation | Reward |
|---|---:|
| Reaching the goal | +10 |
| Hitting an obstacle | -5 |
| Each normal move | -1 |
| Staying at a boundary | -1 |

The objective is to maximize the total reward and reach the goal efficiently.

---

## Graphical Representation

The following grid represents the MDP environment.

```text
+-------+-------+-------+
| START | (0,1) | (0,2) |
+-------+-------+-------+
| (1,0) |   X   | (1,2) |
+-------+-------+-------+
| (2,0) | (2,1) | GOAL  |
+-------+-------+-------+
```

- `START` — Initial state `(0,0)`
- `X` — Obstacle `(1,1)`
- `GOAL` — Destination `(2,2)`

Example transition:

`(0,0) --Right (0.8), Reward (-1)--> (0,1)`

---

## Python Representation

```python
print("Name: Nithish S")
print("Register Number: 212224240105")

states = [
    (0, 0), (0, 1), (0, 2),
    (1, 0), (1, 1), (1, 2),
    (2, 0), (2, 1), (2, 2)
]

actions = ["Up", "Down", "Left", "Right"]

mdp = {
    "states": states,
    "actions": actions,
    "start": (0, 0),
    "goal": (2, 2),
    "obstacle": (1, 1),
    "transition_probability": {
        "intended": 0.8,
        "other": 0.2
    },
    "rewards": {
        "goal": 10,
        "obstacle": -5,
        "normal_move": -1
    },
    "gamma": 0.9
}

print("States:", mdp["states"])
print("Actions:", mdp["actions"])
print("Start State:", mdp["start"])
print("Goal State:", mdp["goal"])
print("Obstacle:", mdp["obstacle"])
print("Transition Probabilities:", mdp["transition_probability"])
print("Rewards:", mdp["rewards"])
print("Discount Factor:", mdp["gamma"])
```

---

## Output

```text
Name: Nithish S
Register Number: 212224240105
States: [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
Actions: ['Up', 'Down', 'Left', 'Right']
Start State: (0, 0)
Goal State: (2, 2)
Obstacle: (1, 1)
Transition Probabilities: {'intended': 0.8, 'other': 0.2}
Rewards: {'goal': 10, 'obstacle': -5, 'normal_move': -1}
Discount Factor: 0.9
```

---

## Result

The robot navigation problem was successfully represented as a Markov Decision Process by defining the state space, action space, transition probabilities, reward function, and discount factor.


