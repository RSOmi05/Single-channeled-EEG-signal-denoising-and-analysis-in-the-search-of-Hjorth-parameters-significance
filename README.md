# Single channeled EEG signal denoising and analysis in the search of Hjorth parameters significance

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)]()

## 📋 Table of Contents
- [Overview](#-overview)
- [Dataset Information](#-dataset-information)
- [Methodology](#-methodology)
- [Results](#-results)
- [Key Findings](#-key-findings)
- [Installation & Usage](#-installation--usage)
- [Dependencies](#-dependencies)
- [Project Structure](#-project-structure)
- [Statistical Analysis](#-statistical-analysis)
- [Future Work](#-future-work)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

## 🧠 Overview

This project presents a comprehensive analysis of single-channel EEG signals focusing on **Hjorth parameters** (Activity, Mobility, and Complexity) through statistical significance testing. The study investigates temporal dynamics and segment-wise variations in neurological signals using advanced signal processing techniques.

## 🎯 Objectives
- Analyze EEG signals in both time and frequency domains
- Implement effective noise removal techniques
- Perform temporal segmentation and statistical analysis
- Evaluate Hjorth parameters significance across different segments
- Compare odd vs even segments statistical differences

## 📊 Dataset Information

| Parameter | Value |
|-----------|-------|
| **Duration** | 190 seconds |
| **Sampling Rate** | 128 Hz |
| **Total Samples** | 24,320 |
| **Segments** | 38 (5-second each) |
| **Channel Type** | Single-channel EEG |

## 🔬 Methodology

### 1. 📈 Signal Visualization
- **Time Domain**: Plotted signal amplitude vs time/samples
- **Frequency Domain**: Power Spectral Density (PSD) using Welch's method
- **Rationale**: PSD provides better noise reduction compared to raw FFT

### 2. 🔧 Noise Removal
- **Bandpass Filter**: 0.5-30 Hz (preserves essential EEG frequencies)
- **Notch Filter**: 50 Hz (removes power-line interference)
- **Result**: Significant reduction in high-frequency artifacts

### 3. ✂️ Signal Segmentation
- Divided 190-second signal into **38 segments** of 5 seconds each
- Calculated mean amplitude per segment
- Generated average waveform across all segments

### 4. 📊 Hjorth Parameters Calculation
For each segment, computed:
- **Activity**: Variance of the signal (signal power)
- **Mobility**: Standard deviation of the derivative (mean frequency)
- **Complexity**: Ratio indicating waveform complexity

## 📈 Results

### Time & Frequency Domain Analysis
![Time Domain](Single-channeled-EEG-signal-denoising-and-analysis-in-the-search-of-Hjorth-parameters-significance/ EEG signal in time domain.png)
*Figure 1: EEG signal in time domain showing 190 seconds of brain electrical activity*

![Frequency Domain](media/image2.jpeg)
*Figure 2: Power spectral density revealing frequency characteristics*

### Noise Removal Results
![Noise Removal](media/image3.jpeg)
*Figure 3: Comparison of original vs filtered EEG signals*

![Frequency Comparison](media/image4.jpeg)
*Figure 4: PSD comparison showing effective high-frequency noise elimination*

### Segmentation Analysis
![Segmentation](media/image5.jpeg)
*Figure 5: (a) Mean amplitude per segment, (b) Average waveform across all segments*

### Hjorth Parameters Distribution
![Hjorth Parameters](media/image6.jpeg)
*Figure 6: Activity, Mobility, and Complexity variations across 38 segments*

![Group Analysis](media/image7.jpeg)
*Figure 7: Hjorth parameters distribution by temporal groups*

## 🔍 Key Findings

### Statistical Significance (Odd vs Even Segments)
| Parameter | t-statistic | p-value | Significance |
|-----------|-------------|---------|--------------|
| **Activity** | -2.1472 | 0.0386 | ✅ **Significant** |
| **Mobility** | 1.8564 | 0.0716 | ❌ Not Significant |
| **Complexity** | -2.4095 | 0.0212 | ✅ **Significant** |

### ANOVA Analysis (4 Temporal Groups)
| Parameter | F-value | p-value | Effect Size (η²) | Significance |
|-----------|---------|---------|------------------|--------------|
| **Activity** | 2.178 | 0.109 | 0.161 | ❌ Not Significant |
| **Mobility** | 3.550 | **0.024** | 0.239 | ✅ **Significant** |
| **Complexity** | 2.797 | 0.055 | 0.198 | ❌ Not Significant |

### 🏆 Key Discoveries
- **Activity & Complexity** show significant differences between odd/even segments
- **Mobility** demonstrates significant temporal changes across recording periods
- Group 3 (segments 21-30) shows distinctive patterns with lowest activity and highest mobility
- Temporal transition occurs around segments 20-21

## 🛠️ Installation & Usage

### Prerequisites
```bash
pip install numpy pandas matplotlib scipy seaborn scikit-learn
```

### Running the Analysis
```python
# Clone the repository
git clone https://github.com/yourusername/single-channel-eeg-hjorth-parameters-statistical-significance-analysis.git

# Navigate to project directory
cd single-channel-eeg-hjorth-parameters-statistical-significance-analysis

# Run the main analysis
python eeg_hjorth_analysis.py
```

## 📦 Dependencies

- **NumPy**: Numerical computations
- **Pandas**: Data manipulation
- **Matplotlib**: Plotting and visualization
- **SciPy**: Signal processing and statistical analysis
- **Seaborn**: Advanced statistical visualizations
- **Scikit-learn**: Machine learning utilities

## 📁 Project Structure

```
├── data/
│   └── eeg_signal_data.xlsx
├── src/
│   ├── signal_processing.py
│   ├── hjorth_parameters.py
│   ├── statistical_analysis.py
│   └── visualization.py
├── results/
│   ├── figures/
│   └── statistical_reports/
├── notebooks/
│   └── EEG_Analysis.ipynb
├── README.md
└── requirements.txt
```

## 📊 Statistical Analysis

### Methodology Applied
- **Paired t-tests** for odd vs even segment comparison
- **One-way ANOVA** for temporal group analysis
- **Effect size calculation** (Cohen's eta-squared)
- **Significance level**: α = 0.05

### Interpretation
The analysis reveals that EEG signals exhibit **temporal heterogeneity** with:
- Significant amplitude and complexity variations between alternating segments
- Notable frequency characteristic changes across recording periods
- Evidence of non-stationary behavior in neural activity

## 🔮 Future Work

- [ ] Multi-channel EEG analysis comparison
- [ ] Machine learning classification based on Hjorth parameters
- [ ] Real-time EEG processing implementation
- [ ] Integration with clinical depression biomarker studies
- [ ] Advanced artifact removal using ICA techniques

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📧 Contact

**Rahat Shahrior**
- Email: rahat.shahriar04@gmail.com
- Phone: +880 1975714851

## 📚 References

- Hjorth, B. (1970). EEG analysis based on time domain properties
- Welch, P. (1967). The use of fast Fourier transform for estimation of power spectra
- Statistical analysis methodology based on established EEG research protocols

---

⭐ **Star this repository if you found it helpful!**
