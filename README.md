# Model-Free Reinforcement Learning

Python implementations of **Monte Carlo, SARSA, and Q-learning** for training agents in Gymnasium’s Blackjack and Cliff Walking environments.

Developed for **WPI DS551/CS551 — Reinforcement Learning**.

## Technologies

Python 3.11 • NumPy • Gymnasium • pynose • VS Code

## Algorithms

| Algorithm | Environment | Learning approach |
|---|---|---|
| First-visit Monte Carlo prediction | Blackjack | Estimates state values under a fixed policy |
| First-visit Monte Carlo control | Blackjack | Learns action values through epsilon-greedy exploration |
| SARSA | Cliff Walking | Updates values using the next selected action |
| Q-learning | Cliff Walking | Updates values using the best estimated next action |

Monte Carlo learns after completing an episode. SARSA and Q-learning learn after each step.

## Features

- Epsilon-greedy action selection to balance exploration and exploitation.
- Discounted returns and first-visit updates for Monte Carlo learning.
- Incremental action-value updates for SARSA and Q-learning.
- Exploration decay in SARSA.
- Automated tests covering policies and learned values.

## Project Structure

```text
model-free-reinforcement-learning/
├── Project2-1/
│   ├── mc.py
│   └── mc_test.py
├── Project2-2/
│   ├── td.py
│   └── td_test.py
└── README.md
```

## Installation

Use **Python 3.11**.

```bash
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install "gymnasium[atari]==1.2.2" pynose==1.5.5 numpy
```

Alternatively, activate an existing Python 3.11 Conda environment:

```bash
conda activate myenv
python -m pip install "gymnasium[atari]==1.2.2" pynose==1.5.5 numpy
```

## Run Tests

From the repository root:

```bash
cd Project2-1
python -m nose -v mc_test.py

cd ../Project2-2
python -m nose -v td_test.py
```

Run an individual test from its corresponding folder:

```bash
# From Project2-1
python -m nose -v mc_test.py:test_mc_prediction

# From Project2-2
python -m nose -v td_test.py:test_sarsa
```

## Verified Test Results

Both supplied test suites passed in a Python 3.11 Conda environment.

| Test suite | Passed | Observed runtime |
|---|---|---|
| Monte Carlo | 5/5 | 89.944 seconds |
| Temporal Difference | 4/4 | 2.497 seconds |

The Monte Carlo suite simulates millions of episodes. Runtime varies by hardware, and stochastic exploration can affect results.

These tests validate the supplied checks; they do not measure performance against other reinforcement learning implementations.

## Debugging

Use VS Code’s Python debugger to inspect:

- States, actions, and rewards returned by the environment.
- Discounted returns calculated after an episode.
- Updates to `V[state]` and `Q[state][action]`.

Set the debugger’s working directory to the folder containing the selected test file. Disable repeated loop breakpoints before completing large training runs.

## Learning Outcomes

- Implementing model-free reinforcement learning algorithms.
- Understanding on-policy and off-policy updates.
- Balancing exploration and exploitation.
- Debugging stochastic algorithms and validating implementations with tests.

## Attribution

Based on starter code and tests from
[UrbanIntelligence/WPI-DS551-Fall26 — Project 2](https://github.com/UrbanIntelligence/WPI-DS551-Fall26/tree/main/Project2).

Original attribution headers are retained in the Python source files.
