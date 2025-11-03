# Theme Park Optimization - Canada's Wonderland

An optimization model to determine the best itinerary for visiting attractions at Canada's Wonderland, minimizing total time spent while maximizing visitor satisfaction.

## Problem Overview

This project optimizes theme park visits by considering:
- **Time-dependent wait times** throughout the day
- **Walking distances** between attractions
- **Ride durations** and visitor **preference scores**
- Park operating hours and constraints

The optimization extends the Traveling Salesman Problem with dynamic wait times and weighted preferences.

## Quick Start

### Prerequisites
- Python 3.12+
- [uv](https://github.com/astral-sh/uv) package manager
- Get uv on Windows: curl -LsSf https://astral.sh/uv/install.sh | sh
- Get uv on Mac: brew install uv

### Installation & Running

```bash
# Install dependencies
uv sync

# Launch Jupyter notebook
uv run jupyter notebook theme_park_optimization.ipynb

```

Then open `theme_park_optimization.ipynb` in your browser.

## Data Structure

All data is stored in CSV files in the `data/` directory:

- **`attractions.csv`**: Attraction IDs, names, preferences (1-10), and ride durations
- **`distances.csv`**: nxn walking time matrix (minutes) between all locations
- **`wait_times.csv`**: Hourly wait times for each attraction (9am-9pm)

## Current Status

The project currently includes:
- Data loading with validation (matrix size, symmetry checks)
- Helper functions for time calculations and wait time interpolation
- Sample itinerary evaluation

## Project Structure

```
.
 theme_park_optimization.ipynb  # Main notebook
 data/
 attractions.csv           # Attraction data
 distances.csv             # Distance matrix
 wait_times.csv            # Hourly wait times
 pyproject.toml            # Project dependencies
```
