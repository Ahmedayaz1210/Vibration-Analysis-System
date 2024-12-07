# Vibration-Analysis-System
Machine learning-based vibration analysis system for early fault detection in industrial bearings using NASA's bearing dataset.

## Project Dashboard
[![Dashboard](https://img.shields.io/badge/Visit-Dashboard-blue?style=for-the-badge&logo=amazonwebservices)](https://dashboard-link-placeholder.com)

**Will add once dashboard is ready, will be made in Django and deployed on AWS or Azure**

By: Ahmed Ayaz
Date: 12/10/2024  

## Important Notes
This project is contained entirely in a single Jupyter notebook: `/final_project/vibration_analysis_system.ipynb`. All code, analysis, visualizations, and detailed documentation can be found in this notebook and directory. Please refer to this file for the complete project implementation.

Addtionally, the dataset contains more than 10,000 files so github was not letting me push all files to repository even if i did set by set. Please download dataset from link provided in references.

---

## Table of Contents

| **Sections**                     |  
|----------------------------------|  
| **Section 1: Introduction**      |  
| **Section 2: Data Analysis and Exploration**  |  
| **Section 3: Signal Processing** |  
| **Section 4: Modeling and Prediction** |  
| **Section 5: Results**           |  
| **Section 6: References**        |  

---

### 1. Introduction
This project develops an intelligent system for early fault detection in industrial bearings using advanced signal processing and machine learning. Utilizing the NASA Bearing Dataset, which captures progression of inner race defects, roller element damage, and outer race deterioration, the system analyzes vibration signatures to detect impending failures before critical damage occurs.

**Key Focus Areas:**
- Early detection through vibration pattern analysis across different failure modes
- Statistical and frequency band analysis to identify reliable deterioration indicators
- Time-domain and frequency-domain characteristic monitoring
- Integration of signal processing with machine learning for pattern recognition

The system aims to optimize maintenance timing, reduce costs, enhance safety, and improve operational efficiency across industrial applications through predictive fault detection.

---

### 2. Data Analysis & Exploration
Initial analysis of the NASA Bearing Dataset focused on understanding vibration patterns across multiple test sets. The exploration process included:

**Data Processing:**
- Dataset 1: 8 channels (2 per bearing)
- Dataset 2 & 3: 4 channels each (1 per bearing)
- 20 Hz sampling rate across all datasets

**Statistical Analysis:**
- Basic metrics (Mean, RMS, Peak-to-Peak)
- Bearing health scoring (0-100 scale)
- Early failure detection patterns
- Channel-wise amplitude variations

**Key Finding:** 
Identified unique roller element failure pattern at 81.3% of lifetime, significantly earlier than other failure modes that typically manifested in the final 10% of operation.

---

### 3. Signal Processing
Advanced signal processing techniques were implemented to extract meaningful patterns from vibration data:

**Key Components:**
- FFT (Fast Fourier Transform) for frequency domain analysis
- Butterworth bandpass filters for signal isolation:
  - Low band (20 Hz - 1 kHz): Basic movement patterns
  - Mid band (1-3 kHz): Early warning indicators
  - High band (3-5 kHz): Damage detection
- Statistical measures: RMS, Peak, Crest Factor, and Kurtosis

**Signal Enhancement:**
- Cascaded filtering for noise reduction
- Multi-channel validation
- Focus on 0-5 kHz range for optimal fault detection


---

### 4. Feature Engineering
Comprehensive feature extraction and analysis were performed to prepare data for machine learning:

**Feature Extraction:**
- Time-domain metrics: RMS, Peak, Crest Factor, Kurtosis
- Frequency bands analysis:
  - Low (20Hz-1kHz): Base rotation
  - Mid (1-3kHz): Early warning
  - High (3-5kHz): Damage detection
- Degradation tracking features

**Dataset Generation:**
- 753 total samples across all failure types
- 5% sampling rate (minimum 20 samples)
- Balanced representation of failure modes
- Channel-specific data collection

**Key Findings:**
- Distinct signatures for each failure type
- Early detection patterns identified
- Strong feature correlations established

---

### 5. Modeling and Prediction
Implementation of Random Forest model for bearing failure prediction and classification:

**Model Setup:**
- Random Forest with 100 estimators
- Dataset split: 72.2% training, 12.7% validation, 15% test
- 20 key features selected across frequency bands and degradation indicators

**Performance:**
- Mean Absolute Error: 67.20 hours
- R² Score: 0.865
- Prediction accuracy:
  - Near-term (1-7 days): High confidence
  - Medium-term (7-14 days): Good reliability
  - Long-term (14+ days): Lower confidence

**Validation Results:**
- Early-life accuracy: 94-95%
- Mid-life accuracy: 77-99%
- Late-stage accuracy: 34-96%

---

### 6. References & Dependencies

**Dataset:**
- NASA Bearing Dataset: [Kaggle](https://www.kaggle.com/datasets/vinayak123tyagi/bearing-dataset/data)
- IMS Bearing Dataset: Raw vibration signal data from the NSF I/UC Center for Intelligent Maintenance Systems (IMS), University of Cincinnati

**Libraries Used:**
- Data Processing:
  - `numpy`: Numerical computing
  - `pandas`: Data manipulation
  - `scipy`: Signal processing and FFT analysis

- Visualization:
  - `matplotlib`: Basic plotting
  - `seaborn`: Statistical visualization

- Machine Learning:
  - `scikit-learn`: Random Forest implementation and metrics
  - `joblib`: Model saving and loading
  - `pathlib`: File path handling

**Installation:**
```python
pip install numpy pandas matplotlib seaborn scipy scikit-learn joblib
```

---
