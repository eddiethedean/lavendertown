# LavenderTown Examples

This directory contains example applications demonstrating LavenderTown usage.

## CSV Upload App

The `app.py` file is a standalone Streamlit application that allows you to upload CSV files and analyze them for data quality issues.

### Running the App

1. Make sure you have LavenderTown installed:
```bash
pip install lavendertown
```

2. Navigate to the examples directory:
```bash
cd examples
```

3. Run the Streamlit app:
```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

### Features

- **CSV File Upload**: Drag and drop or browse to upload CSV files
- **Automatic Encoding Detection**: Tries multiple encodings (UTF-8, Latin-1, etc.)
- **Dataset Preview**: See basic statistics and first rows of your data
- **Interactive Analysis**: Full LavenderTown data quality inspection with:
  - Null value detection
  - Type inconsistency detection
  - Outlier detection
  - Interactive visualizations
  - Filtering and drill-down capabilities

### Usage Tips

- Supported file formats: CSV files (`.csv`)
- File size: Up to 200MB recommended
- Encoding: Automatically detects UTF-8, Latin-1, ISO-8859-1, or CP1252
- For very large files, consider sampling the data first for faster analysis

### Example Workflow

1. Upload a CSV file using the file uploader
2. Review the dataset preview to confirm the data loaded correctly
3. Explore the data quality findings in the sidebar
4. Use filters to focus on specific issues
5. View detailed visualizations and problematic rows
6. Export findings if needed (future feature)

