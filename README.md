# Power Grid Intelligence: Predictive Maintenance & Failure Detection
# Team: 
| Team Member | GitHub Repo                    | Presubmission Document         |
|-------------|--------------------------------|--------------------------------|
1. Vaibhav
2. Ravin
3. Ashok                                       | ashokkumar.8three@gmail.com
4. Rajini


## Overview

This capstone project develops machine learning models to predict equipment failures and maintenance requirements for power grid utilities. By analyzing operational metrics, environmental factors, and historical maintenance data, the project aims to enable proactive maintenance strategies that minimize grid downtime and reduce operational costs.

## Business Problem

Unplanned power grid failures impact millions of customers and result in significant revenue loss and regulatory penalties. Current maintenance approaches rely heavily on scheduled intervals rather than equipment condition. This project addresses:

- **Equipment Failures**: Predict which grid assets will fail in the near future
- **Maintenance Optimization**: Identify assets requiring urgent maintenance before failures occur
- **Cost Reduction**: Minimize emergency repairs and customer downtime
- **Regulatory Compliance**: Reduce penalty costs through improved asset management

## Dataset Overview

**File**: `PowerGrid_Utility_Intelligence_orig.csv`

**Size**: 10,000+ equipment records with 33 operational and environmental features

### Key Features

#### Asset Information
- `asset_id`: Unique equipment identifier
- `asset_type`: Equipment classification (Transmission Line, Switchgear, Circuit Breaker, Transformer, Substation)
- `asset_age_years`: Equipment age in years
- `manufacturer`: Equipment manufacturer (ABB, Schneider, GE, Siemens, Hitachi)
- `substation_region`: Geographic region (Central, North, South, East, West)

#### Operational Metrics
- `power_load_mw`: Current power load in megawatts
- `load_utilization_pct`: Load utilization as percentage of capacity
- `voltage_fluctuation_pct`: Deviation from standard voltage
- `frequency_deviation_hz`: Deviation from 50/60 Hz standard
- `transformer_temperature_c`: Equipment operating temperature
- `oil_quality_score`: Quality score for transformer oil (0-100)

#### Equipment Health
- `equipment_health_score`: Overall health assessment (0-100)
- `vibration_level`: Equipment vibration measurements
- `inspection_score`: Recent inspection results
- `maintenance_overdue_days`: Days since last scheduled maintenance
- `maintenance_events_last_12m`: Count of maintenance events in past year

#### Outage & Service Quality
- `previous_outages_12m`: Number of outages in past 12 months
- `avg_outage_duration_minutes`: Average duration of outages
- `customer_complaints_last_12m`: Number of customer complaints
- `customers_served`: Number of customers dependent on asset

#### Environmental Factors
- `temperature_c`: Ambient temperature
- `humidity_pct`: Environmental humidity
- `wind_speed_kmh`: Wind speed conditions
- `rainfall_mm`: Rainfall in past period
- `storm_risk_index`: Risk index for weather events

#### Financial Impact
- `estimated_revenue_loss`: Estimated loss from equipment downtime
- `regulatory_penalty_cost`: Penalties from regulatory non-compliance
- `power_load_mw`: Impacts revenue generation

#### Target Variable
- `grid_failure_flag`: Binary target (0: No failure, 1: Failure occurred)

#### Administrative
- `legacy_asset_code`: Legacy system identifier
- `grid_cluster_id`: Cluster assignment for grouping similar assets
- `monitoring_batch_id`: Monitoring batch identifier
- `administrative_reference`: Administrative tracking reference

## Project Goals

1. **Build Predictive Models**: Develop ML models to classify assets at risk of failure
2. **Feature Engineering**: Create meaningful features from operational metrics
3. **Model Comparison**: Evaluate multiple algorithms (Logistic Regression, Random Forest, Gradient Boosting, etc.)
4. **Interpretability**: Identify key factors driving equipment failures
5. **Actionable Insights**: Provide recommendations for maintenance prioritization

## Key Project Documents

**Requirements & Planning**:
- [Problem Statement](docs/requirements/Problem%20Statement.docx) - Project scope and objectives
- [Presubmission Plan](docs/requirements/CP%20Presubmission%20Plan%20_%20Prof.%20Babji.pdf) - Project timeline and milestones

**Reference Materials**:
- [Academic Paper 1](docs/reference/1705.07874v2.pdf) - ML techniques for predictive maintenance
- [Academic Paper 2](docs/reference/1905.04610v1.pdf) - Power systems and ML applications  
- [DSO White Paper](docs/reference/DSO-White-Paper.pdf) - Distribution system operations best practices

See [docs/README.md](docs/README.md) for complete documentation index.

## Expected Outcomes

- Classification model with high recall to catch failures early
- Feature importance analysis highlighting critical maintenance indicators
- Asset risk segmentation for targeted maintenance strategies
- Cost-benefit analysis of preventive vs. reactive maintenance

## Project Structure

```
.
├── README.md                           # Project documentation
├── requirements.txt                    # Python dependencies
├── data/
│   ├── raw/                           # Original dataset
│   │   └── PowerGrid_Utility_Intelligence_orig.csv
│   └── processed/                     # Cleaned & engineered features
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb  # Data exploration
│   ├── 02_feature_engineering.ipynb   # Feature creation
│   └── 03_model_development.ipynb     # Model training & evaluation
├── src/
│   ├── __init__.py
│   ├── data_preprocessing.py          # Data cleaning functions
│   ├── feature_engineering.py         # Feature creation functions
│   ├── model_training.py              # Model training utilities
│   └── evaluation.py                  # Evaluation metrics
├── tests/
│   └── __init__.py
├── results/
│   ├── model_results.json             # Model performance metrics
│   ├── feature_importance.csv         # Feature importance rankings
│   └── predictions.csv                # Model predictions
├── docs/
│   ├── README.md                      # Documentation overview
│   ├── requirements/                  # Problem statements & requirements
│   ├── reference/                     # Reference documents & external materials
│   └── analysis_report.md             # Detailed analysis report
├── deliverables/
│   ├── README.md                      # Deliverables overview
│   ├── pre_submission/                # Documents for management review
│   ├── reports/                       # Final analysis & technical reports
│   └── presentations/                 # Presentation materials & slide decks
└── config/
    └── config.yaml                    # Configuration parameters
```

## Installation & Setup

### Prerequisites
- Python 3.8+
- pip or conda package manager
- Git

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd iitm-capstone-powergrid-intelligence
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify installation**
   ```bash
   python -c "import pandas, sklearn; print('Setup successful!')"
   ```

## Data Dictionary

| Feature | Type | Unit | Range | Description |
|---------|------|------|-------|-------------|
| asset_id | int | - | 100000+ | Unique asset identifier |
| asset_type | str | - | 5 types | Equipment classification |
| asset_age_years | float | years | 0-40 | Age of equipment |
| power_load_mw | float | MW | 20-290 | Current power load |
| load_utilization_pct | float | % | 30-99 | Utilization percentage |
| transformer_temperature_c | float | °C | 45-95 | Operating temperature |
| equipment_health_score | float | score | 0-100 | Health assessment |
| grid_failure_flag | int | binary | 0,1 | Target: failure occurred |

## Usage

### Run EDA Notebook
```bash
jupyter notebook notebooks/01_exploratory_analysis.ipynb
```

### Train Models
```python
from src.model_training import train_pipeline
results = train_pipeline(data_path='data/raw/PowerGrid_Utility_Intelligence_orig.csv')
```

### Generate Predictions
```python
from src.evaluation import predict_asset_risk
predictions = predict_asset_risk(model, new_data)
```

## Key Findings (To be updated)

- [EDA insights to be documented]
- [Feature correlations]
- [Model performance metrics]
- [Critical failure indicators]

## Model Performance (To be updated)

| Model | Accuracy | Precision | Recall | F1-Score | AUC-ROC |
|-------|----------|-----------|--------|----------|---------|
| Baseline | - | - | - | - | - |
| Model 1 | - | - | - | - | - |
| Model 2 | - | - | - | - | - |

*Results to be populated after model training*

## Key Insights (To be updated)

### Risk Factors
- High temperature and vibration levels are strong failure indicators
- Equipment older than 30 years shows increased failure rates
- High load utilization combined with maintenance overdue days increases risk

### Recommendations
1. Prioritize maintenance for assets with high vibration levels
2. Monitor temperature trends closely for transformer equipment
3. Implement preventive maintenance for assets over 30 years old
4. Balance load distribution to reduce equipment stress

## Technologies & Libraries

- **Data Processing**: Pandas, NumPy
- **Machine Learning**: Scikit-learn, XGBoost, LightGBM
- **Visualization**: Matplotlib, Seaborn, Plotly
- **Jupyter**: JupyterLab for interactive analysis
- **Version Control**: Git

## Team & Collaboration

- **Project Type**: IITM Capstone (Domain 7 - Power Grid Intelligence)
- **Batch**: Pravarthak Batch 02
- **Mentor**: [To be added]

## Contributing

1. Create a feature branch: `git checkout -b feature/your-feature-name`
2. Commit changes: `git commit -am 'Add new feature'`
3. Push to branch: `git push origin feature/your-feature-name`
4. Submit pull request with detailed description

## File Naming Conventions

- Python files: `snake_case.py`
- Notebooks: `##_descriptive_name.ipynb`
- Results: `result_type_date.csv` (e.g., `predictions_20260628.csv`)

## Troubleshooting

### Common Issues

**Issue**: Missing data columns
- **Solution**: Verify CSV file has all 33 columns; check for encoding issues

**Issue**: Import errors
- **Solution**: Run `pip install -r requirements.txt` again; verify Python version

**Issue**: Memory errors with large dataset
- **Solution**: Use `chunksize` parameter when reading CSV; consider subsampling for testing

## References & Resources

- [Dataset Source](../iitm-pravarthak-batch02/Domain7_Capstone/Domain%207/Dataset/)
- [Project Documentation](docs/README.md) - Problem statements, requirements, and reference materials
- [Presubmission Plan](docs/requirements/CP%20Presubmission%20Plan%20_%20Prof.%20Babji.pdf) - Approved project timeline
- [Academic Papers](docs/reference/) - ML and power systems research
- Power Grid Standards & Regulations
- Predictive Maintenance Best Practices
- Machine Learning Classification Techniques

## License

This project is part of IITM's Data Science Capstone Program.

## Contact & Support

For questions or issues related to this project, please reach out through the project repository or IITM channels.

---

**Last Updated**: June 28, 2026
**Status**: In Progress
**Next Milestone**: Exploratory Data Analysis (EDA) Complete
