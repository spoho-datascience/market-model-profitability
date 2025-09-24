# Economic Paper: Rating Systems and Betting Strategies

This repository contains the code and data for economic experiments analyzing rating systems and betting strategies in sports forecasting.

## Project Description

The research investigates the relationship between forecast accuracy and betting profitability using:
- ELO rating systems for team strength estimation
- Log function forecasts for probability prediction
- Kelly and fixed betting strategies
- Real-world football data and artificial simulations

## Requirements

- Python 3.7
- Dependencies listed in `requirements.txt` or `pyproject.toml`

## Environment Setup

This project supports two Python environment management approaches:

### Option 1: Using uv (Recommended - Fastest)

[uv](https://github.com/astral-sh/uv) is a fast Python package installer and resolver.

1. Install uv:
```bash
# On macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# On Windows
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

2. Create and activate environment:
```bash
# Create virtual environment with Python 3.7
uv venv --python 3.7

# Activate environment
# On macOS/Linux:
source .venv/bin/activate
# On Windows:
.venv\Scripts\activate

# Install dependencies
uv pip install -e .
```

### Option 2: Using venv and pip

Traditional Python environment setup:

1. Create virtual environment:
```bash
# Ensure Python 3.7 is installed
python3.7 -m venv venv

# Activate environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Running Experiments

1. **Real Data Experiment**:
```bash
jupyter notebook EconomicExperimentRealData.ipynb
```

2. **Artificial Data Experiment**:
```bash
jupyter notebook EconomicExperimentArtificialData.ipynb
```

### Data Files

- `network.csv`: Network data with team ratings and match results
- `Results_*.xlsx`: Experiment output files
- `LICENSE`: Apache 2.0 license

## Project Structure

```
├── EconomicExperimentRealData.ipynb    # Real data analysis
├── EconomicExperimentArtificialData.ipynb  # Simulation experiments
├── network.csv                         # Network/match data
├── Results_*.xlsx                      # Experiment results
├── requirements.txt                    # Dependencies for venv
├── pyproject.toml                      # Project config for uv
├── .gitignore                          # Git ignore rules
└── README.md                           # This file
```

## Dependencies

The project requires the `dfg_rating` package, which should be installed separately. Main dependencies include:

- pandas (>=1.1.0, <1.4.0) - Data manipulation
- numpy (>=1.16.0, <1.22.0) - Numerical computing
- tqdm (>=4.50.0, <5.0.0) - Progress bars
- jupyter (>=1.0.0) - Notebook environment
- openpyxl (>=3.0.0, <4.0.0) - Excel export

## Reproducibility

This repository is configured for 100% reproducibility:
- Fixed Python 3.7 requirement
- Pinned dependency versions
- Deterministic experiment parameters
- Version-controlled data and code

## License

Licensed under the Apache License 2.0. See `LICENSE` file for details.
