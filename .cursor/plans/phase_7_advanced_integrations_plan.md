# Phase 7: Advanced Integrations - Implementation Plan

**Status:** Planning  
**Estimated Timeline:** 6-8 weeks  
**Version Target:** v0.8.0

## Overview

Phase 7 focuses on advanced integrations that enhance visualization capabilities, analysis depth, and infrastructure. This phase will add:
1. Plotly interactive visualizations
2. tsfresh time-series features
3. Streamlit Extras UI components
4. SQLAlchemy database backend
5. Joblib parallel detector execution

## Goals

- Enhance visualization with interactive charts
- Improve time-series analysis with advanced feature extraction
- Polish UI with additional components
- Enable scalable collaboration with database backend
- Optimize performance with parallel execution

---

## Task 1: Plotly Interactive Visualizations

### Objective
Add Plotly as an optional visualization backend while keeping Altair as default. Enable interactive charts for time-series and 3D outlier visualizations.

### Implementation Steps

#### 1.1 Add Plotly Dependency
- [ ] Add `plotly>=5.0.0` to `pyproject.toml` optional dependencies
- [ ] Create `[plotly]` extra group
- [ ] Update installation documentation

#### 1.2 Create Plotly Visualization Module
- [ ] Create `lavendertown/ui/visualizations/plotly_charts.py`
- [ ] Implement `render_plotly_charts()` function
- [ ] Support for:
  - Time-series line charts with zoom/pan
  - 3D scatter plots for outlier visualization
  - Interactive bar charts for ghost type distribution
  - Heatmaps for correlation analysis

#### 1.3 Create Visualization Backend Abstraction
- [ ] Create `lavendertown/ui/visualizations/base.py` with backend protocol
- [ ] Implement `AltairBackend` (existing)
- [ ] Implement `PlotlyBackend` (new)
- [ ] Add configuration option to choose backend (default: Altair)

#### 1.4 Integrate with Charts Component
- [ ] Update `lavendertown/ui/charts.py` to support backend selection
- [ ] Add UI toggle for visualization backend
- [ ] Maintain backward compatibility (Altair default)

#### 1.5 Testing
- [ ] Unit tests for Plotly backend
- [ ] Integration tests with Inspector
- [ ] Test fallback when Plotly not installed
- [ ] Performance benchmarks

### Files to Create/Modify
- `lavendertown/ui/visualizations/__init__.py` (new)
- `lavendertown/ui/visualizations/base.py` (new)
- `lavendertown/ui/visualizations/plotly_charts.py` (new)
- `lavendertown/ui/charts.py` (modify)
- `pyproject.toml` (modify)
- `tests/test_ui_plotly.py` (new)

### Dependencies
- `plotly>=5.0.0` (optional)

### Estimated Time: 1.5 weeks

---

## Task 2: tsfresh Time-Series Features

### Objective
Integrate tsfresh for advanced time-series feature extraction. Extract 700+ time-series features for ML-based anomaly detection.

### Implementation Steps

#### 2.1 Add tsfresh Dependency
- [ ] Add `tsfresh>=0.20.0` to `pyproject.toml` optional dependencies
- [ ] Create `[timeseries]` extra group (may already exist)
- [ ] Update installation documentation

#### 2.2 Create Feature Extraction Module
- [ ] Create `lavendertown/detectors/timeseries_features.py`
- [ ] Implement `extract_tsfresh_features()` function
- [ ] Support feature selection and filtering
- [ ] Handle both Pandas and Polars DataFrames

#### 2.3 Enhance TimeSeriesAnomalyDetector
- [ ] Update `lavendertown/detectors/timeseries.py`
- [ ] Add `use_tsfresh_features` parameter
- [ ] Integrate feature extraction into detection pipeline
- [ ] Use extracted features for ML-based anomaly detection

#### 2.4 Create Feature Analysis Component
- [ ] Create `lavendertown/ui/timeseries_features.py`
- [ ] Display extracted features in UI
- [ ] Show feature importance/ranking
- [ ] Allow feature selection for analysis

#### 2.5 Testing
- [ ] Unit tests for feature extraction
- [ ] Integration tests with TimeSeriesAnomalyDetector
- [ ] Test with various time-series datasets
- [ ] Performance benchmarks

### Files to Create/Modify
- `lavendertown/detectors/timeseries_features.py` (new)
- `lavendertown/detectors/timeseries.py` (modify)
- `lavendertown/ui/timeseries_features.py` (new)
- `pyproject.toml` (modify)
- `tests/test_detectors_timeseries_features.py` (new)

### Dependencies
- `tsfresh>=0.20.0` (optional)

### Estimated Time: 2 weeks

---

## Task 3: Streamlit Extras UI Components

### Objective
Add Streamlit Extras components for enhanced UI. Better tables, badges, card layouts, and additional widgets.

### Implementation Steps

#### 3.1 Add Streamlit Extras Dependency
- [ ] Add `streamlit-extras>=0.3.0` to `pyproject.toml` optional dependencies
- [ ] Create `[ui]` extra group
- [ ] Update installation documentation

#### 3.2 Identify Components to Integrate
- [ ] Research available streamlit-extras components
- [ ] Select components that enhance UX:
  - `st.metric_card()` for better metric display
  - `st.badges()` for status indicators
  - `st.card()` for card layouts
  - `st.dataframe()` enhancements
  - `st.toggle()` for better toggles

#### 3.3 Create Enhanced UI Components
- [ ] Create `lavendertown/ui/extras.py`
- [ ] Wrap streamlit-extras components with fallbacks
- [ ] Implement graceful degradation when not installed
- [ ] Create enhanced versions of existing components

#### 3.4 Integrate with Existing UI
- [ ] Update `lavendertown/ui/overview.py` to use metric cards
- [ ] Update `lavendertown/ui/table.py` to use enhanced tables
- [ ] Add badges to findings display
- [ ] Use cards for better layout organization

#### 3.5 Testing
- [ ] Unit tests for enhanced components
- [ ] Test fallback behavior
- [ ] UI/UX testing

### Files to Create/Modify
- `lavendertown/ui/extras.py` (new)
- `lavendertown/ui/overview.py` (modify)
- `lavendertown/ui/table.py` (modify)
- `pyproject.toml` (modify)
- `tests/test_ui_extras.py` (new)

### Dependencies
- `streamlit-extras>=0.3.0` (optional)

### Estimated Time: 1 week

---

## Task 4: SQLAlchemy Database Backend

### Objective
Add database backend option for collaboration features. Replace file-based storage with SQLAlchemy (SQLite for local, PostgreSQL for multi-user).

### Implementation Steps

#### 4.1 Add SQLAlchemy Dependency
- [ ] Add `sqlalchemy>=2.0.0` to `pyproject.toml` optional dependencies
- [ ] Add `psycopg2-binary>=2.9.0` for PostgreSQL support
- [ ] Create `[database]` extra group
- [ ] Update installation documentation

#### 4.2 Design Database Schema
- [ ] Design tables for:
  - Reports (id, title, author, created_at, findings_json)
  - Annotations (id, report_id, finding_id, author, comment, tags, status)
  - RuleSets (id, name, description, rules_json)
- [ ] Create migration system (Alembic or simple versioning)

#### 4.3 Create Database Storage Backend
- [ ] Create `lavendertown/collaboration/database_storage.py`
- [ ] Implement `DatabaseStorage` class
- [ ] Support SQLite (default) and PostgreSQL
- [ ] Implement CRUD operations for reports and annotations
- [ ] Add querying and filtering capabilities

#### 4.4 Update Storage Interface
- [ ] Create storage backend abstraction in `lavendertown/collaboration/storage.py`
- [ ] Update `FileStorage` to implement same interface
- [ ] Add configuration for storage backend selection
- [ ] Support migration from file-based to database storage

#### 4.5 Add Database Configuration
- [ ] Add database URL configuration to `lavendertown/config.py`
- [ ] Support environment variables:
  - `LAVENDERTOWN_DATABASE_URL` (default: SQLite)
  - `LAVENDERTOWN_DATABASE_TYPE` (sqlite/postgresql)
- [ ] Add connection pooling for PostgreSQL

#### 4.6 Update Collaboration API
- [ ] Update `lavendertown/collaboration/api.py` to use storage abstraction
- [ ] Add query methods for historical reports
- [ ] Add filtering and search capabilities
- [ ] Maintain backward compatibility with file storage

#### 4.7 Testing
- [ ] Unit tests for database storage
- [ ] Integration tests with SQLite
- [ ] Integration tests with PostgreSQL (optional)
- [ ] Migration tests from file to database
- [ ] Performance benchmarks

### Files to Create/Modify
- `lavendertown/collaboration/database_storage.py` (new)
- `lavendertown/collaboration/storage.py` (modify)
- `lavendertown/collaboration/api.py` (modify)
- `lavendertown/config.py` (modify)
- `pyproject.toml` (modify)
- `tests/test_collaboration_database.py` (new)

### Dependencies
- `sqlalchemy>=2.0.0` (optional)
- `psycopg2-binary>=2.9.0` (optional, for PostgreSQL)

### Estimated Time: 2.5 weeks

---

## Task 5: Joblib Parallel Detector Execution

### Objective
Add parallel execution of detectors for large datasets using Joblib. Speed up analysis by running independent detectors concurrently.

### Implementation Steps

#### 5.1 Add Joblib Dependency
- [ ] Add `joblib>=1.3.0` to `pyproject.toml` optional dependencies
- [ ] Create `[parallel]` extra group
- [ ] Update installation documentation

#### 5.2 Analyze Detector Dependencies
- [ ] Identify which detectors can run in parallel
- [ ] Map detector dependencies (which detectors need results from others)
- [ ] Create dependency graph for detectors

#### 5.3 Create Parallel Execution Module
- [ ] Create `lavendertown/detectors/parallel.py`
- [ ] Implement `ParallelDetectorExecutor` class
- [ ] Support configurable number of workers
- [ ] Handle detector dependencies
- [ ] Implement progress tracking for parallel execution

#### 5.4 Update Inspector
- [ ] Modify `lavendertown/inspector.py` to support parallel execution
- [ ] Add `parallel=True` parameter to `__init__`
- [ ] Add `n_jobs` parameter for worker count
- [ ] Fallback to sequential execution if Joblib not available
- [ ] Add configuration option for default parallel execution

#### 5.5 Optimize for Large Datasets
- [ ] Implement chunking for very large datasets
- [ ] Add memory management for parallel execution
- [ ] Optimize data sharing between workers
- [ ] Add progress indicators for parallel execution

#### 5.6 Testing
- [ ] Unit tests for parallel execution
- [ ] Integration tests with Inspector
- [ ] Performance benchmarks (sequential vs parallel)
- [ ] Test with various dataset sizes
- [ ] Test dependency handling

### Files to Create/Modify
- `lavendertown/detectors/parallel.py` (new)
- `lavendertown/inspector.py` (modify)
- `lavendertown/config.py` (modify)
- `pyproject.toml` (modify)
- `tests/test_detectors_parallel.py` (new)

### Dependencies
- `joblib>=1.3.0` (optional)

### Estimated Time: 1.5 weeks

---

## Integration & Testing

### Cross-Task Integration
- [ ] Ensure all features work together
- [ ] Test Plotly with parallel execution
- [ ] Test tsfresh features with database storage
- [ ] Test UI extras with all features

### Documentation
- [ ] Update README with Phase 7 features
- [ ] Create user guides for each feature
- [ ] Add API documentation
- [ ] Update examples
- [ ] Add migration guides (file to database)

### Version Bump
- [ ] Bump version to 0.8.0
- [ ] Update CHANGELOG
- [ ] Update version mapping

---

## Success Criteria

### Plotly
- [ ] Interactive charts work for time-series data
- [ ] 3D outlier visualization functional
- [ ] Backend selection works in UI
- [ ] Graceful fallback when Plotly not installed

### tsfresh
- [ ] Can extract 700+ features from time-series data
- [ ] Features integrated into anomaly detection
- [ ] UI displays feature information
- [ ] Performance acceptable for typical datasets

### Streamlit Extras
- [ ] Enhanced UI components visible in app
- [ ] Better UX with cards, badges, etc.
- [ ] Graceful fallback when not installed
- [ ] No breaking changes to existing UI

### SQLAlchemy
- [ ] Database storage works with SQLite
- [ ] PostgreSQL support functional
- [ ] Migration from file storage works
- [ ] Querying and filtering work correctly
- [ ] Performance acceptable for typical workloads

### Joblib
- [ ] Parallel execution faster than sequential for large datasets
- [ ] Dependency handling works correctly
- [ ] Progress tracking functional
- [ ] Memory usage acceptable
- [ ] Graceful fallback when not installed

---

## Risk Mitigation

### Technical Risks
1. **Plotly performance**: May be slower than Altair for large datasets
   - Mitigation: Keep Altair as default, make Plotly optional
   
2. **tsfresh memory usage**: Feature extraction can be memory-intensive
   - Mitigation: Add chunking and sampling options
   
3. **Database migration complexity**: Migrating from file to database may be complex
   - Mitigation: Provide clear migration scripts and documentation
   
4. **Parallel execution overhead**: May not be faster for small datasets
   - Mitigation: Auto-detect optimal execution mode based on dataset size

### Dependencies Risks
1. **Heavy dependencies**: Some packages are large
   - Mitigation: All dependencies are optional, users choose what to install
   
2. **Version conflicts**: Dependencies may conflict with user's environment
   - Mitigation: Use flexible version requirements, test compatibility

---

## Timeline

**Week 1-2:**
- Task 1: Plotly Interactive Visualizations
- Task 3: Streamlit Extras UI Components (can work in parallel)

**Week 3-4:**
- Task 2: tsfresh Time-Series Features

**Week 5-6:**
- Task 4: SQLAlchemy Database Backend

**Week 7-8:**
- Task 5: Joblib Parallel Detector Execution
- Integration testing
- Documentation
- Version bump and release

---

## Notes

- All features should be optional dependencies
- Maintain backward compatibility
- Provide graceful fallbacks when dependencies not installed
- Focus on user experience improvements
- Performance should be equal or better than current implementation
- All features should be well-tested and documented

