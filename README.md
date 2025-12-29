# LavenderTown

A Streamlit-first Python package for detecting and visualizing "data ghosts": type inconsistencies, nulls, invalid values, schema drift, and anomalies in tabular datasets.

## Installation

```bash
pip install lavendertown
```

## Quick Start

### Basic Usage with Pandas

```python
from lavendertown import Inspector
import pandas as pd

# Load your data
df = pd.read_csv("your_data.csv")

# Create inspector and render
inspector = Inspector(df)
inspector.render()
```

### Using Polars

```python
from lavendertown import Inspector
import polars as pl

# Load your data with Polars
df = pl.read_csv("your_data.csv")

# Create inspector and render (works with Polars too!)
inspector = Inspector(df)
inspector.render()
```

To use Polars support, install with the optional dependency:
```bash
pip install lavendertown[polars]
```

### CSV Upload App

Run the example Streamlit app for interactive CSV upload and analysis:

```bash
streamlit run examples/app.py
```

### Dataset Comparison (Drift Detection)

Compare datasets to detect schema and distribution changes:

```python
from lavendertown import Inspector
import pandas as pd

baseline_df = pd.read_csv("baseline.csv")
current_df = pd.read_csv("current.csv")

inspector = Inspector(current_df)
drift_findings = inspector.compare_with_baseline(
    baseline_df=baseline_df,
    comparison_type="full"  # or "schema_only", "distribution_only"
)

# Drift findings have ghost_type="drift"
for finding in drift_findings:
    if finding.ghost_type == "drift":
        print(f"{finding.column}: {finding.description}")
```

### Custom Rules

Create custom data quality rules using the Streamlit UI:
1. Click "Manage Rules" in the sidebar
2. Create rules (range, regex, or enum types)
3. Rules are automatically executed with each analysis
4. Export/import rules as JSON for reuse

## Features

- **Zero-config data quality insights** - Get started with minimal setup
- **Streamlit-native UI** - No HTML embeds, fully integrated with Streamlit
- **Interactive ghost detection** - Drill down into problematic rows
- **Pandas & Polars support** - Works with your existing data pipelines
- **CSV Upload App** - Ready-to-use Streamlit app for uploading and analyzing CSV files
- **Exportable findings** - Download results as JSON or CSV with one click
- **Dataset Comparison** - Detect schema and distribution drift between datasets
- **Custom Rules** - Create and manage custom data quality rules via UI

## Ghost Categories

LavenderTown detects four main categories of data ghosts:

1. **Structural Ghosts** - Mixed dtypes, schema drift, unexpected nullability
2. **Value Ghosts** - Out-of-range values, regex violations, enum violations
3. **Completeness Ghosts** - Null density thresholds, conditional nulls
4. **Statistical Ghosts** - Outliers (IQR, Z-score, MAD), distribution shifts

## License

MIT License - see [LICENSE](LICENSE) file for details.

## CSV Upload App

For interactive analysis, use the included Streamlit app:

```bash
streamlit run examples/app.py
```

This opens a web interface where you can:
- Upload CSV files via drag-and-drop or file browser
- Preview your data before analysis
- View interactive data quality insights
- Export findings with download buttons

See [examples/README.md](examples/README.md) for detailed usage instructions.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

