# Rating Systems and Betting Strategies

**Replication package for:**

*"Does the consideration of market prices in model selection increase model profitability? Evidence from theory, artificial data and real-world data."*

By Wunderlich, F., Garnica-Caparros, M., and Memmert, D. (2025)

[![License](https://img.shields.io/badge/license-See%20Paper-blue)]()
[![Python](https://img.shields.io/badge/python-3.7+-blue)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange)](https://jupyter.org/)

## Overview

This replication package generates the 4 figures (Fig 1-4) and provides all information for the 4 tables (Table 3-6) from the paper.

## Repository Structure

```
├── data/          # Anonymized real-world dataset
├── figures/       # R code to generate Figures 1-4
├── experiments/   # Jupyter notebooks for experiments
└── results/       # Experimental results storage
```

### Data
- `data_real_anonymised.csv` - Anonymized dataset (team names and match dates) used for Figure 3 and real-world data results (Tables 5-6)

### Figures
- `Figure_3_FavoriteLongshot.Rmd` - Generates Figure 3
- `Figures_124_OLR.Rmd` - Generates Figures 1, 2, and 4
- Generated figures are saved in this directory

### Experiments
- `EconomicExperimentRealData.ipynb` - Real-world data experiments
- `EconomicExperimentArtificialData.ipynb` - Artificial data experiments

### Results
Experimental results are automatically saved with descriptive filenames:
- Format: `{data_type}_{result_type}_{betting_strategy}_{odds_type}.xlsx`
- Example: `real_raw_fixed_averageodds.xlsx` = real data, raw results, fixed betting, average odds
The folder contains all result files from the runs presented in the paper. Rerunning will lead to an automatic reproduction of these result files.

## Requirements

- **Python**: 3.7+ (tested with 3.7)
- **R**: For figure generation (Rmd files)
- **Dependencies**: Listed in `requirements.txt` and `pyproject.toml`

## Environment Setup

This project supports two Python environment management approaches:

### Option 1: Using uv (Recommended)

[uv](https://github.com/astral-sh/uv) is a fast Python package installer and resolver.

1. **Install uv:**
   ```bash
   # macOS/Linux
   curl -LsSf https://astral.sh/uv/install.sh | sh

   # Windows
   powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

2. **Setup environment:**
   ```bash
   # Create virtual environment
   uv venv --python 3.7

   # Activate environment
   source .venv/bin/activate  # macOS/Linux
   .venv\Scripts\activate     # Windows

   # Install dependencies
   uv pip install -e .
   ```

### Option 2: Using pip + venv

1. **Create virtual environment:**
   ```bash
   python3.7 -m venv venv

   # Activate environment
   source venv/bin/activate  # macOS/Linux
   venv\Scripts\activate     # Windows
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Running Experiments

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Open notebooks:**
   - `EconomicExperimentRealData.ipynb` - Real data experiments
   - `EconomicExperimentArtificialData.ipynb` - Artificial data experiments

## Key Dependencies

| Package | Version | Purpose |
|---------|---------|----------|
| pandas | >=1.1.0, <1.4.0 | Data manipulation |
| numpy | >=1.16.0, <1.22.0 | Numerical computing |
| tqdm | >=4.50.0, <5.0.0 | Progress bars |
| jupyter | >=1.0.0 | Notebook environment |
| openpyxl | >=3.0.0, <4.0.0 | Excel export |
| dfg_rating | - | Simulation framework |

> **Note:** The `dfg_rating` package must be installed from [GitHub](https://github.com/spoho-datascience/dfg-rating).

## Citation

If you use this code or data in your research, please cite:

```bibtex
@article{wunderlich2025rating,
  title={Does the consideration of market prices in model selection increase model profitability? Evidence from theory, artificial data and real-world data},
  author={Wunderlich, F. and Garnica-Caparros, M. and Memmert, D.},
  year={2025}
}
```

## Replication Instructions

### Figures 1-4
Run the R Markdown files in R to generate and save figures:
- No additional steps required
- Figures saved automatically to `/figures/`

### Tables 3-6
**Runtime:** Several minutes (Table 5 & 6) to >1 hour (Table 3 & 4) per experimental run
**Requirements:**
- Table 3 & 5: 1 run each (direct replication)
- Table 4 & 6: Multiple runs required (results gathered from multiple files)

**Total runs needed:**
- Artificial data: 3 experimental runs
- Real data: 6 experimental runs

### Table 3 (Artificial Data)
1. Open `EconomicExperimentArtificialData.ipynb`
2. Set configuration: `config = experimentFL`
3. Run complete notebook
4. **Result:** `artificial_table_ExperimentFL_Fixed_bm2.xlsx`

### Table 4 (Artificial Data)
Requires 3 experimental runs with different configurations:

1. **Run 1:** `config = experimentFL` (same as Table 3)
2. **Run 2:** `config = experimentHA`
3. **Run 3:** `config = experimentDraw`

**Result files mapping:**
| Strategy | Fixed 10% | Fixed 0% | Kelly 10% | Kelly 0% |
|----------|-----------|----------|-----------|----------|
| Favourite-Longshot | ExperimentFL_Fixed_bm2 | ExperimentFL_Fixed_bm1 | ExperimentFL_Kelly_bm2 | ExperimentFL_Kelly_bm1 |
| Home Advantage | ExperimentHA_Fixed_bm2 | ExperimentHA_Fixed_bm1 | ExperimentHA_Kelly_bm2 | ExperimentHA_Kelly_bm1 |
| Draw | ExperimentDraw_Fixed_bm2 | ExperimentDraw_Fixed_bm1 | ExperimentDraw_Kelly_bm2 | ExperimentDraw_Kelly_bm1 |

### Table 5 (Real Data)
1. Open `EconomicExperimentRealData.ipynb`
2. Set parameters:
   ```python
   betting = FixedBetting(100)
   betting_description = 'fixed'
   odds_type = 'averageodds'
   ```
3. Run complete notebook
4. **Result:** `real_table_fixed_averageodds.xlsx` (includes confidence intervals)

### Table 6 (Real Data)
Requires 6 experimental runs with different betting/odds combinations:

| Odds Type | Fixed | Threshold | Kelly |
|-----------|-------|-----------|-------|
| **Average** | FixedBetting(100) | ThresholdBetting(0.2) | KellyBetting(100) |
| **Maximum** | FixedBetting(100) | ThresholdBetting(0.3) | KellyBetting(100) |

**Result files:**
- `real_table_fixed_averageodds.xlsx`
- `real_table_threshold_averageodds.xlsx`
- `real_table_kelly_averageodds.xlsx`
- `real_table_fixed_maximumodds.xlsx`
- `real_table_threshold_maximumodds.xlsx`
- `real_table_kelly_maximumodds.xlsx`

## Troubleshooting

### Common Issues

**Environment Setup:**
- Ensure Python 3.7+ is installed
- Try creating a fresh virtual environment if packages conflict
- On Windows, use appropriate activation script (.bat vs .ps1)

**Missing Dependencies:**
```bash
# If dfg_rating is missing, install from GitHub:
pip install git+https://github.com/spoho-datascience/dfg-rating.git
```

**Jupyter Issues:**
```bash
# Register kernel with environment
python -m ipykernel install --user --name=economic_paper
```

**Long Runtime:**
- Due to the number of model iterations per run and the number of different runs for full result reproduction, running time may be important to consider 
- Orignial runs on real-world data needed ~20 mins each on a laptop with 16 GB RAM
- Original runs on artificial data needed ~ 2 hours each on a laptop with 16 GB RAM
- Consider running overnight for complete reproduction
- Monitor progress bars in notebooks

## Contributing

This is a replication package for a published paper. For questions or issues:

1. Check existing issues in the repository
2. Create a new issue with detailed description
3. Include system information and error messages

## License

This project is released under the terms specified by the authors. Please see the paper for usage rights and restrictions.