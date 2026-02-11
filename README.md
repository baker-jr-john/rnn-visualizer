# RNN Visualizer

An interactive tool for understanding Recurrent Neural Network (RNN) calculations by hand.

**Live Demo:** [johnbaker.io/rnn-visualizer](https://johnbaker.io/rnn-visualizer/)

## Overview

This tool visualizes how an RNN processes sequential data step-by-step, based on the calculations from [Can You Calculate an RNN by Hand?](https://www.byhand.ai/p/2-can-you-calculate-an-rnn-by-hand).

## Features

- **Editable Inputs & Weights** - Click on orange (input) or yellow (weight) cells to modify values
- **Auto-Recalculation** - Hidden states and outputs update automatically when you change values
- **Dependency Tracing** - Click on green (hidden state) or blue (output) cells to visualize which values contribute to the calculation
- **Step-by-Step Breakdown** - See detailed arithmetic for each calculation with color-coded values

## RNN Architecture

The tool demonstrates a simple RNN with:
- 2-dimensional hidden state (h₁, h₂)
- 4 time steps
- ReLU activation on h₁, no activation on h₂

### Formulas

| Component | Formula |
|-----------|---------|
| Hidden h₁ | `ReLU(x × Wₓₕ[0] + h₁_prev × Wₕₕ[0,0] + h₂_prev × Wₕₕ[0,1])` |
| Hidden h₂ | `x × Wₓₕ[1] + h₁_prev × Wₕₕ[1,0] + h₂_prev × Wₕₕ[1,1]` |
| Output y  | `h₁ × Wₕᵧ[0] + h₂ × Wₕᵧ[1]` |

## Usage

1. **Edit values** - Click any orange or yellow cell and type a new number, press Enter to confirm
2. **Trace dependencies** - Click any green or blue cell to see its formula and calculation breakdown
3. **Reset** - Click the Reset button or click the same cell again to clear the trace

## License

MIT
