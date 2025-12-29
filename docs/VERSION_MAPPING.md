# Feature Version Mapping

This document maps features to the PyPI versions where they were introduced.

## Version History

### v0.1.0 - v0.2.0 (Initial Release)
**Phase 0-1: MVP Features**

- Core Inspector class
- Pandas support
- Streamlit-native UI
- Null detection (`NullGhostDetector`)
- Type inconsistency detection (`TypeGhostDetector`)
- Basic outlier detection (`OutlierGhostDetector`)
- CSV upload UI (basic)
- Findings export (JSON/CSV)

### v0.3.0
**Phase 2: Power Features**

- Polars support
- Rule authoring UI (range, regex, enum rules)
- Dataset comparison (drift detection)
- Performance optimizations
- Theme support

### v0.4.0
**Phase 3: Ecosystem Integration**

- Pandera rule export
- Great Expectations export
- CLI wrapper (Click framework)
- Streamlit Cloud deployment support

### v0.5.0
**Phase 4-5: Advanced Features & Quick Wins**

**Phase 4: Advanced Ghosts**
- Time-series anomaly detection
- Cross-column validation rules
- ML-assisted anomaly detection (scikit-learn: Isolation Forest, LOF, One-Class SVM)
- Collaboration features (annotations, shareable reports)

**Phase 5: Quick Wins**
- Rich CLI output enhancement
- orjson JSON serialization (2-3x faster)
- Hypothesis property-based testing
- python-dotenv configuration management

### v0.6.0
**Phase 6: Feature Enhancements**

- Enhanced File Upload component (drag-and-drop, animated progress, automatic encoding detection)
- Typer CLI framework
- PyOD anomaly detection (40+ algorithms)
- Ruptures change point detection
- scipy.stats statistical tests (Kolmogorov-Smirnov, chi-square)
- PyArrow Parquet export
- Faker test data generation utilities
- ydata-profiling integration

## Feature Quick Reference

| Feature | Version | Notes |
|--------|---------|-------|
| Core Inspector | v0.1.0 | Foundation |
| Null Detection | v0.1.0 | MVP |
| Type Detection | v0.1.0 | MVP |
| Outlier Detection | v0.1.0 | MVP |
| Polars Support | v0.3.0 | Phase 2 |
| Custom Rules UI | v0.3.0 | Phase 2 |
| Drift Detection | v0.3.0 | Phase 2 |
| Pandera Export | v0.4.0 | Phase 3 |
| Great Expectations Export | v0.4.0 | Phase 3 |
| CLI Tool | v0.4.0 | Phase 3 |
| Time-Series Anomalies | v0.5.0 | Phase 4 |
| Cross-Column Rules | v0.5.0 | Phase 4 |
| ML Anomaly Detection | v0.5.0 | Phase 4 (scikit-learn), v0.6.0 (PyOD) |
| Collaboration Features | v0.5.0 | Phase 4 |
| Rich CLI Output | v0.5.0 | Phase 5 |
| orjson Fast JSON | v0.5.0 | Phase 5 |
| Configuration Management | v0.5.0 | Phase 5 |
| Enhanced File Upload | v0.6.0 | Phase 6 |
| Typer CLI | v0.6.0 | Phase 6 |
| PyOD Algorithms | v0.6.0 | Phase 6 |
| Change Point Detection | v0.6.0 | Phase 6 |
| Statistical Tests | v0.6.0 | Phase 6 |
| Parquet Export | v0.6.0 | Phase 6 |
| Data Profiling | v0.6.0 | Phase 6 |

