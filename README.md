# Ad Campaign Time-Series Labeler

Detects turning points and changepoints in ad campaign time-series data using LOESS smoothing and multi-scale changepoint detection.

## Features
- LOESS smoothing for trend extraction
- L2 multi-scale changepoint detection via `ruptures`
- 15 primary pattern labels (e.g. "Increasing then decreasing", "Flat / Stationary")
- Secondary labels: Seasonal, Cyclical, Volatility clustering, Transient spikes, etc.
- Confidence scoring per series
- Auto-generates plots for every series

## Setup
1. Open `ad_campaign_labeler.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Upload your `time_series_anonymized.xlsx` when prompted
3. Run All cells

## Outputs (generated locally, not tracked in repo)
- `time_series_tp_labels_collab.xlsx` — label results for every series
- `ts_label_plots_tp_collab/` — per-series PNG plots with LOESS trend, turning points, and changepoints

## Dependencies
Installed automatically in the first cell:
```
ruptures, openpyxl
```

## Tuning Parameters
All knobs are in one place at the top of the notebook:

| Parameter | Default | Effect |
|---|---|---|
| `LOESS_FRAC` | 0.20 | Smoothing tightness |
| `TP_MIN_AMPLITUDE` | 0.15 | Minimum swing to count as turning point |
| `PEN_TIGHT / MEDIUM / LOOSE` | 0.5 / 1.5 / 3.0 | Changepoint sensitivity |
| `MAX_CPS` | 7 | Max changepoints per series |

## Note
Data files (`.xlsx`) and output folders are excluded from this repo via `.gitignore`.