# Neural Non-negative Matrix Factorization Analysis of Optogenetic Data

## 🧠 Research Overview

This repository contains the implementation and analysis of **Neural Non-negative Matrix Factorization (Neural NMF)** applied to optogenetic stimulation data from mouse brain recordings. The research focuses on decomposing neural activity patterns into interpretable motifs and evaluating their correspondence with optogenetic stimulation events.

### 🔬 Scientific Objectives

1. **Motif Discovery**: Extract hierarchical neural motifs from CLa (Central Lateral Amygdala) recordings
2. **Stimulation-Response Analysis**: Quantify how neural motifs respond to optogenetic stimulation
3. **Architecture Optimization**: Determine optimal Neural NMF configurations for neuroscience data
4. **Performance Evaluation**: Develop F1-score framework for motif validation

## 📊 Methodology

### Neural NMF Architecture

- **Two-layer hierarchical decomposition**: S ≈ W¹ × W² × H
- **W¹**: Maps neurons to lower-level temporal patterns
- **W²**: Combines low-level patterns into higher-level motifs
- **H**: Temporal activations of higher-level motifs

### Data Processing Pipeline

1. **Temporal Segmentation**: Sliding window approach for time-series analysis
2. **Unsupervised Learning**: 20-epoch training with lr=500
3. **Optogenetic Analysis**: Post-stimulation response window analysis
4. **Performance Metrics**: F1-score evaluation across activation thresholds

## 📁 Repository Structure

```
repo/
├── code/
│   ├── FinalFile.ipynb          # Main analysis notebook (fully annotated)
│   ├── *.png                    # Generated figures and visualizations
│   └── outdated_code/           # Legacy development files
├── extra/                       # Additional analysis results
├── README.md                    # This file
```

### Key Files

- **`FinalFile.ipynb`**: Complete research pipeline with comprehensive annotations
- **Visualization outputs**: High-resolution IEEE-standard figures
  - `W1.png`: Lower-level basis matrix heatmap
  - `W.png`: Higher-level basis matrix heatmap
  - `H.png`: Post-stimulation activation patterns
  - `heatmap_W2_H.png`: Reconstructed neural activity
  - `f1_score_vs_threshold.png`: Performance evaluation curves
  - `row_*_bar_graph_*.png`: Individual motif analysis

## 🛠️ Requirements

```python
# Core Dependencies
torch                    # Neural network implementation
numpy                   # Numerical computing
scipy                   # Signal processing and MATLAB file loading
matplotlib              # Visualization
scikit-learn           # Machine learning utilities
pandas                 # Data manipulation

# Custom Modules
NeuralNMF              # Neural NMF implementation
```

## 🚀 Usage

### 1. Data Preparation

```python
import scipy.io
mat_data = scipy.io.loadmat("Opto_Data_CLa{mouse_id}.mat")
```

### 2. Run Analysis

```python
# Execute main analysis pipeline
layers = [40, 10]  # Architecture: [hidden_dim, motif_dim]
history = NNMF(mat_data, layers, day=0, mouse=18, timeframes=1)
```

### 3. Hyperparameter Optimization

```python
# Systematic architecture evaluation
losses, k1s, k2s = evaluate_hyperparameters(mat_data, day=0, mouse=18)
```

## 📈 Key Findings

### 🏆 Optimal Configuration

- **Best Architecture**: K₁=10, K₂=10 (Normalized Loss: 0.913)
- **Training Efficiency**: ~1.1 seconds per epoch, 22.3 seconds total
- **Performance**: Successfully identified motifs corresponding to optogenetic stimulation

### 🧪 Scientific Contributions

#### Methodological Advances

- First application of Neural NMF to optogenetic data analysis
- Hierarchical decomposition for complex neural pattern analysis
- Quantitative F1-score framework for motif validation

#### Neuroscience Insights

- Demonstrated neural motif-stimulation correspondence
- Characterized post-stimulation activity dynamics in CLa region
- Established temporal response patterns following optogenetic intervention

#### Technical Innovations

- Reproducible analysis pipeline with comprehensive documentation
- IEEE-compliant visualization standards for publication
- Systematic hyperparameter optimization methodology

## 📊 Performance Metrics

| Metric          | Value        |
| --------------- | ------------ |
| Optimal K₁      | 10           |
| Optimal K₂      | 10           |
| Normalized Loss | 0.913        |
| Training Time   | 22.3 seconds |
| F1-Score Range  | 0.0 - 0.8    |

## 🔬 Research Applications

### Immediate Applications

- **Neural motif characterization** in optogenetic experiments
- **Stimulation-response quantification** for closed-loop systems
- **Architecture optimization** for neural data analysis

### Future Directions

- Multi-day longitudinal studies
- Cross-mouse validation experiments
- Real-time motif detection systems
- Behavioral correlation analysis
- Pharmacological intervention studies

## 📝 Citation

If you use this code or methodology in your research, please cite:

```bibtex
@software{neural_nmf_optogenetic_2024,
  title={Neural Non-negative Matrix Factorization for Optogenetic Data Analysis},
  author={[Your Name]},
  year={2024},
  url={https://github.com/[your-username]/[repo-name]}
}
```

## 📧 Contact

For questions about the methodology, implementation, or research collaboration:

- **Research Inquiries**: [your.email@institution.edu]
- **Technical Support**: [Create an issue in this repository]

## 🏛️ Institution

**Research conducted at**: [Your Institution]  
**Department**: [Your Department]  
**Lab**: [Your Lab Name]

## 📜 License

This research code is provided for academic and research purposes. Please see LICENSE file for detailed terms.

---

**Keywords**: Neural NMF, Optogenetics, Neuroscience, Motif Analysis, CLa, Mouse Brain, Machine Learning, Signal Processing
