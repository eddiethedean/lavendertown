# LavenderTown

> A Streamlit-first Python package for detecting and visualizing "data ghosts": type inconsistencies, nulls, invalid values, schema drift, and anomalies in tabular datasets.

LavenderTown helps you quickly identify data quality issues in your datasets through an intuitive, interactive Streamlit interface. Perfect for data scientists, analysts, and engineers who need to understand their data quality before diving into analysis.

## Features

!!! info "Version Information"
    See [Version Mapping](VERSION_MAPPING.md) for details on when features were introduced.

- **[Zero-config data quality insights](user-guide/basic-usage.md)** - Get started with minimal setup
- **[Streamlit-native UI](user-guide/basic-usage.md)** - Fully integrated with Streamlit, no HTML embeds
- **[Interactive ghost detection](user-guide/basic-usage.md)** - Drill down into problematic rows
- **[Pandas & Polars support](user-guide/basic-usage.md#backend-detection)** - Works with your existing data pipelines
- **[Exportable findings](user-guide/basic-usage.md)** - Download results as JSON, CSV, or Parquet
- **[Dataset Comparison](user-guide/drift-detection.md)** - Detect schema and distribution drift with statistical tests
- **[Custom Rules](user-guide/custom-rules.md)** - Create and manage custom data quality rules via UI
- **[Enhanced File Upload](api-reference/upload.md)** - Drag-and-drop with animated progress and automatic encoding detection
- **[Modular UI Components](guides/modular-ui-components.md)** - Flexible component system for customizing the Inspector interface
- **[Interactive Visualizations](api-reference/visualizations.md)** - Plotly backend with zoom, pan, and 3D visualizations
- **[Advanced Time-Series Features](api-reference/timeseries_features.md)** - tsfresh integration for 700+ time-series features
- **[Enhanced UI Components](guides/modular-ui-components.md)** - Streamlit Extras for improved metric cards and badges
- **[Database Backend](api-reference/database_storage.md)** - SQLAlchemy support for SQLite and PostgreSQL
- **[High Performance](guides/performance.md)** - Optimized for datasets up to millions of rows
- **[Enhanced CLI Tool](user-guide/cli.md)** - Interactive CLI with progress bars and formatted output
- **[Ecosystem Integration](api-reference/export/pandera.md)** - Export rules to Pandera and Great Expectations
- **[Configuration Management](api-reference/config.md)** - Environment-based configuration with `.env` files
- **[Advanced ML Detection](user-guide/ml-anomaly-detection.md)** - 40+ ML anomaly detection algorithms via PyOD
- **[Time-Series Analysis](user-guide/time-series.md)** - Change point detection and comprehensive profiling
- **[Statistical Testing](user-guide/drift-detection.md)** - Kolmogorov-Smirnov and chi-square tests for drift detection

## Quick Start

```python
import streamlit as st
from lavendertown import Inspector
import pandas as pd

# Load your data
df = pd.read_csv("your_data.csv")

# Create inspector and render
inspector = Inspector(df)
inspector.render()  # This must be called within a Streamlit app context
```

That's it! Save this code in a file (e.g., `app.py`) and run `streamlit run app.py` to see the interactive data quality dashboard.

## Installation

```bash
pip install lavendertown
```

For optional features:

```bash
# Polars support
pip install lavendertown[polars]

# Ecosystem integrations
pip install lavendertown[pandera]
pip install lavendertown[great_expectations]

# Enhanced CLI with Rich formatting
pip install lavendertown[cli]

# ML and time-series features
pip install lavendertown[ml]          # PyOD + scikit-learn for 40+ ML algorithms
pip install lavendertown[timeseries]  # Ruptures + statsmodels + tsfresh for time-series analysis
pip install lavendertown[profiling]   # ydata-profiling for comprehensive reports
pip install lavendertown[parquet]     # PyArrow for Parquet export
pip install lavendertown[stats]       # scipy.stats for statistical tests

# Phase 7 features (v0.7.0)
pip install lavendertown[plotly]      # Plotly for interactive visualizations
pip install lavendertown[ui]          # Streamlit Extras for enhanced UI components
pip install lavendertown[database]    # SQLAlchemy for database backend

# All optional dependencies
pip install lavendertown[all]
```

## Documentation

- **[Getting Started](getting-started/installation.md)** - Installation and quick start guide
- **[User Guide](user-guide/basic-usage.md)** - Comprehensive usage documentation
- **[API Reference](api-reference/inspector.md)** - Complete API documentation
- **[Examples](guides/examples.md)** - Code examples and tutorials
- **[Design Documentation](design/architecture.md)** - Architecture and design decisions

## Ghost Categories

LavenderTown detects four main categories of data quality issues:

1. **Structural Ghosts** - Mixed dtypes, schema drift, unexpected nullability
2. **Value Ghosts** - Out-of-range values, regex violations, enum violations  
3. **Completeness Ghosts** - Null density thresholds, conditional nulls
4. **Statistical Ghosts** - Outliers (IQR method), distribution shifts

Each finding includes:
- **Ghost type**: Category of the issue
- **Column**: Affected column name
- **Severity**: `info`, `warning`, or `error`
- **Description**: Human-readable explanation
- **Row indices**: Specific rows affected (when applicable)
- **Metadata**: Additional diagnostic information

## Links

- **GitHub Repository**: https://github.com/eddiethedean/lavendertown
- **PyPI Package**: https://pypi.org/project/lavendertown/
- **Issues**: https://github.com/eddiethedean/lavendertown/issues

---

**Made with ❤️ for the data quality community**

