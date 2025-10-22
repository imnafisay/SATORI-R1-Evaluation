# SATORI-R1-Evaluation

Reproduction and evaluation of the SATORI-R1 multimodal reasoning model on benchmark datasets.

## 📊 Results

### MMStar Benchmark

| Category | Paper (SATORI-3B) | My Evaluation | Difference |
|----------|-------------------|----------------|------------|
| **Overall** | **55.9%** | **55.8%** | **-0.1%** ✅ |
| Coarse Perception | 68.0% | 68.4% | +0.4% |
| Fine-grained Perception | 50.4% | 50.4% | 0.0% |
| Instance Reasoning | 60.8% | 60.4% | -0.4% |
| Logical Reasoning | 54.0% | 52.4% | -1.6% |
| Math | 62.0% | 62.0% | 0.0% |
| Science & Technology | 40.0% | 41.2% | +1.2% |

### OCRBench
*Evaluation in progress...*

## 🔧 Setup

### Hardware
- **Platform:** Google Colab Pro
- **GPU:** NVIDIA A100 (40GB)

### Model
- **Base Model:** Qwen2.5-VL-3B-Instruct
- **Framework:** VLMEvalKit

## 📁 Repository Structure
```
SATORI-R1-Evaluation/
├── README.md
├── results/
│   └── MMStar_results.xlsx
└── notebooks/
    └── SATORI_Evaluation.ipynb
```

## 🚀 How to Run

1. Clone the SATORI-R1 repository
2. Set up VLMEvalKit evaluation framework
3. Download the SATORI-3B model
4. Run evaluation on desired benchmarks

## 📝 Citation

Original Paper:
```bibtex
@article{shen2025satori,
  title={SATORI-R1: Incentivizing Multimodal Reasoning with Spatial Grounding and Verifiable Rewards},
  author={Shen, Chuming and Wei, Wei and Qu, Xiaoye and Cheng, Yu},
  journal={arXiv preprint arXiv:2505.19094},
  year={2025}
}
```

## 🔗 Links

- [Original Paper](https://arxiv.org/abs/2505.19094)
- [Official Repository](https://github.com/justairr/SATORI-R1)
