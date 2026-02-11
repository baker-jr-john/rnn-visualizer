# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file interactive RNN visualizer (`index.html`) hosted on GitHub Pages at johnbaker.io/rnn-visualizer. No build process - edit and push to deploy.

## Development

Open `index.html` directly in a browser to test changes. Push to `main` branch to deploy.

## Architecture

Everything is in `index.html`:
- **Weights grid (rows 2-3)**: Wₓₕ, Wₕₕ, Wₕᵧ matrices - all editable with `contenteditable`
- **Computation grid (rows 6-10)**: Initial state (row 6), then 4 time steps with inputs, hidden states, and outputs
- **Calculation panel**: Shows step-by-step arithmetic when tracing a cell

Key JavaScript functions:
- `recalculate()` - Propagates changes through all time steps when any input/weight changes
- `trace(cellId)` - Highlights dependencies and shows calculation breakdown
- `generateCalculation(cellId)` - Builds the step-by-step arithmetic HTML
- `clearHighlights()` - Resets visual state

## RNN Formulas

```
h₁ = ReLU(x × Wₓₕ[0] + h₁_prev × Wₕₕ[0,0] + h₂_prev × Wₕₕ[0,1])
h₂ = x × Wₓₕ[1] + h₁_prev × Wₕₕ[1,0] + h₂_prev × Wₕₕ[1,1]
y  = h₁ × Wₕᵧ[0] + h₂ × Wₕᵧ[1]
```

## Cell ID Mapping

| Cell | Content |
|------|---------|
| B2, B3 | Wₓₕ weights |
| D2, E2, D3, E3 | Wₕₕ weights |
| G2, H2 | Wₕᵧ weights |
| B7-B10 | Inputs (x) |
| C7-C10 | Hidden h₁ |
| D7-D10 | Hidden h₂ |
| F7-F10 | Outputs (y) |
