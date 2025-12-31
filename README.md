# Hopfield Network - Pattern Recovery Simulation

A Python implementation of Hopfield Network demonstrating associative memory and energy minimization.

## Overview

This project explores how Hopfield Networks store and recover patterns using Hebbian learning. The network minimizes energy to converge from noisy inputs to stored patterns.

## Mathematical Background

### Weight Matrix (Hebbian Learning)
```
W = p · pᵀ,  where Wᵢᵢ = 0
```

### Energy Function
```
E = -½ ΣᵢΣⱼ Wᵢⱼ · sᵢ · sⱼ
```

### Neuron Update Rule
```
sᵢ = sign(Σⱼ Wᵢⱼ · sⱼ)
```

## Stored Pattern

```
pattern = [+1, +1, +1, -1, -1, -1, +1, +1, -1, -1]
```

## Experiments

| Experiment | Flipped Bits | Initial Accuracy | Final Accuracy | Energy Change | Result |
|------------|--------------|------------------|----------------|---------------|--------|
| Q6 (3 bits) | 0, 3, 7 | 7/10 | 10/10 | -3 → -45 | ✓ Recovered |
| Q7 (4 bits) | 0, 3, 5, 7 | 6/10 | 10/10 | +3 → -45 | ✓ Recovered |
| Q8 (all bits) | 0-9 | 0/10 | 0/10 | -45 → -45 | ✗ Spurious State |

## Experiment Details

### Q6: 3 Noisy Bits
- Flipped bits: 0, 3, 7
- Network successfully recovers the original pattern
- Energy decreases in 3 steps (one for each corrupted bit)

### Q7: 4 Noisy Bits  
- Flipped bits: 0, 3, 5, 7
- Network still recovers the original pattern
- Higher initial energy due to more corruption

### Q8: All Bits Flipped (Spurious Attractor)
- All 10 bits flipped → creates inverted pattern
- **No recovery!** Network stays in inverted state
- Energy remains constant at -45 (already at minimum)
- Demonstrates that inverted pattern (-p) is also a stable attractor

## Key Findings

1. **Energy Always Decreases**: Network never increases energy during updates
2. **Robust Recovery**: Successfully recovers patterns with up to 40% noise
3. **Spurious States**: Inverted pattern is a stable attractor with same energy as original
4. **Limitation**: Hopfield network cannot distinguish between p and -p

## Project Structure

```
├── Hopfield.ipynb          # Original notebook
├── hopfield_q6.ipynb       # 3 noisy bits experiment
├── hopfield_q7.ipynb       # 4 noisy bits experiment
├── hopfield_q8.ipynb       # All bits flipped experiment
└── images/
    ├── energy_plot_q6.png
    ├── energy_plot_q7.png
    └── energy_plot_q8.png
```

## Requirements

```
numpy
matplotlib
```

## Usage

Open any `.ipynb` file in Jupyter Notebook or Google Colab and run all cells.

## Course Info

- **Course**: Deep Learning
- **Assignment**: Activity 5 - Hopfield Network
- **University**: University of Kurdistan

## License

Educational purposes only.