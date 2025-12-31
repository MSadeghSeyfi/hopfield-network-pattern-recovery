# Hopfield Network - Pattern Recovery Simulation

A Python implementation of a simple Hopfield Network demonstrating associative memory and energy minimization for pattern recovery.

## Overview

This project implements a Hopfield Network to explore how neural networks can store and recover patterns using Hebbian learning. The network demonstrates the concept of energy minimization as it converges from a noisy input to the stored pattern.

## Features

- **Hebbian Learning**: Weight matrix computation using outer product rule
- **Energy Function**: Implementation of the Hopfield energy function
- **Asynchronous Updates**: Sequential neuron updates with immediate state propagation
- **Visualization**: Energy minimization plots showing network convergence
- **Pattern Recovery Analysis**: Comparison of noisy input vs recovered output

## Mathematical Background

### Weight Matrix (Hebbian Learning)
$$W = p \cdot p^T, \quad W_{ii} = 0$$

### Energy Function
$$E = -\frac{1}{2} \sum_{i} \sum_{j} W_{ij} \cdot s_i \cdot s_j$$

### Neuron Update Rule
$$s_i^{new} = \text{sign}\left(\sum_{j} W_{ij} \cdot s_j\right)$$

## Project Structure

```
├── Hopfield.ipynb          # Original Jupyter notebook
├── hopfield_q6.py          # 3 noisy bits experiment
├── hopfield_q7.py          # 4 noisy bits experiment
├── hopfield_q8.py          # All bits flipped experiment
├── energy_plot_q6.png      # Energy plot for 3 noisy bits
├── energy_plot_q7.png      # Energy plot for 4 noisy bits
├── energy_plot_q8.png      # Energy plot for all bits flipped
└── README.md
```

## Experiments

### Experiment 1: 3 Noisy Bits (Baseline)
- **Flipped bits**: 0, 3, 7
- **Initial accuracy**: 7/10
- **Final accuracy**: 10/10 ✓
- **Energy reduction**: -3.0 → -45.0

### Experiment 2: 4 Noisy Bits
- **Flipped bits**: 0, 3, 5, 7
- **Initial accuracy**: 6/10
- **Final accuracy**: 10/10 ✓
- **Energy reduction**: +3.0 → -45.0

### Experiment 3: All Bits Flipped
- **Flipped bits**: All 10 bits
- **Result**: Converges to inverted pattern (spurious attractor)

## Requirements

```
numpy
matplotlib
```

## Usage

```bash
# Run basic experiment
python hopfield_q6.py

# Run with 4 noisy bits
python hopfield_q7.py

# Run with all bits flipped
python hopfield_q8.py
```

## Key Findings

1. **Energy Always Decreases**: The network never increases energy during updates
2. **Robust Recovery**: Network successfully recovers patterns with up to 40% noise
3. **Spurious States**: Inverted patterns are stable attractors (energy minima)
4. **Capacity Limits**: Single pattern storage allows robust recovery

## Course Information

- **Course**: Deep Learning
- **Assignment**: Activity 5 - Hopfield Network
- **Institution**: University of Kurdistan, Department of Computer and IT Engineering

## References

- Hopfield, J.J. (1982). "Neural networks and physical systems with emergent collective computational abilities"
- Hertz, J., Krogh, A., & Palmer, R.G. (1991). "Introduction to the Theory of Neural Computation"

## License

This project is for educational purposes.