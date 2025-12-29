# Examples

LavenderTown includes comprehensive examples demonstrating various usage patterns and features.

## Quick Start

The simplest way to get started is with the CSV upload app:

```bash
streamlit run examples/app.py
```

This app allows you to:
- Upload CSV files via drag-and-drop
- Preview your data
- Analyze data quality interactively
- Export findings as JSON or CSV

## Example Scripts

### 1. Basic Usage

**File:** `examples/basic_usage.py`

Demonstrates the simplest way to use LavenderTown with a Pandas DataFrame.

```bash
streamlit run examples/basic_usage.py
```

**Features:**
- Creating an Inspector with sample data
- Detecting various data quality issues
- Using the Streamlit UI to visualize findings

### 2. Programmatic Usage

**File:** `examples/programmatic_usage.py`

Shows how to use LavenderTown programmatically without the Streamlit UI.

```bash
PYTHONPATH=. python examples/programmatic_usage.py
```

**Features:**
- Getting findings programmatically
- Filtering findings by type and severity
- Processing findings in your own code
- Working without Streamlit

### 3. Drift Detection

**File:** `examples/drift_detection.py`

Demonstrates dataset comparison and drift detection capabilities.

```bash
streamlit run examples/drift_detection.py
```

**Features:**
- Comparing two datasets
- Detecting schema changes
- Detecting distribution changes
- Visualizing drift findings

### 4. Polars Example

**File:** `examples/polars_example.py`

Shows how to use LavenderTown with Polars DataFrames for better performance.

```bash
streamlit run examples/polars_example.py
```

**Prerequisites:**
```bash
pip install lavendertown[polars]
```

**Features:**
- Creating a Polars DataFrame
- Automatic backend detection
- Performance benefits of Polars

### 5. Time-Series Anomaly Detection

**File:** `examples/timeseries_example.py`

Demonstrates detecting anomalies in time-series data.

```bash
streamlit run examples/timeseries_example.py
```

**Prerequisites:**
```bash
pip install lavendertown[timeseries]
```

**Features:**
- Z-score anomaly detection
- Moving average deviation detection
- Seasonal decomposition
- Configurable sensitivity and window size

### 6. ML-Assisted Anomaly Detection

**File:** `examples/ml_anomaly_example.py`

Shows how to use machine learning algorithms to detect complex anomalies.

```bash
streamlit run examples/ml_anomaly_example.py
```

**Prerequisites:**
```bash
pip install lavendertown[ml]
```

**Features:**
- Isolation Forest algorithm
- Local Outlier Factor (LOF)
- One-Class SVM
- Multi-dimensional anomaly detection

### 7. Cross-Column Validation Rules

**File:** `examples/cross_column_rules_example.py`

Demonstrates validating relationships between multiple columns.

```bash
streamlit run examples/cross_column_rules_example.py
```

**Features:**
- Equality checks between columns
- Comparison rules
- Arithmetic validation
- Conditional logic
- Referential integrity checks

### 8. Collaboration Features

**File:** `examples/collaboration_example.py`

Shows how to use annotations and shareable reports for team collaboration.

```bash
streamlit run examples/collaboration_example.py
```

**Features:**
- Adding annotations to findings
- Tagging and status tracking
- Creating shareable reports
- Importing/exporting reports

## Usage Patterns

See the [examples README](https://github.com/eddiethedean/lavendertown/tree/main/examples/README.md) for detailed usage patterns and code examples.

## Running Examples

All examples can be run directly:

```bash
# Streamlit examples
streamlit run examples/[example_name].py

# Python scripts
PYTHONPATH=. python examples/[example_name].py
```

## Customizing Examples

All examples can be customized:

1. **Replace sample data** with your own DataFrame
2. **Modify detection thresholds** by creating custom detectors
3. **Add custom rules** using the rule authoring UI
4. **Export findings** to integrate with your workflow

## Next Steps

- Explore the [User Guide](../user-guide/basic-usage.md) for comprehensive documentation
- Check out the [API Reference](../api-reference/inspector.md) for detailed API documentation
- Review the [Examples README](https://github.com/eddiethedean/lavendertown/tree/main/examples/README.md) for more details

