# SATORI-R1-Evaluation

Reproduction and evaluation of the SATORI-R1 multimodal reasoning model on benchmark datasets.

## Results

### MMStar Benchmark

| Category | Paper (SATORI-3B) | Our Evaluation | Difference |
|----------|-------------------|----------------|------------|
| **Overall** | **55.9%** | **55.8%** | **-0.1%** ✅ |
| Coarse Perception | 68.0% | 68.4% | +0.4% |
| Fine-grained Perception | 50.4% | 50.4% | 0.0% |
| Instance Reasoning | 60.8% | 60.4% | -0.4% |
| Logical Reasoning | 54.0% | 52.4% | -1.6% |
| Math | 62.0% | 62.0% | 0.0% |
| Science & Technology | 40.0% | 41.2% | +1.2% |

### OCRBench

| Metric | Paper (SATORI-3B) | Our Evaluation | Difference |
|--------|-------------------|----------------|------------|
| **Final Score** | **~765** | **764** | **-1** ✅ |
| Final Score (Normalized) | - | 76.4% | - |

**Category Breakdown:**
- Text Recognition: 250
- Scene Text-centric VQA: 170
- Doc-oriented VQA: 144
- Key Information Extraction: 161
- Handwritten Math Expression Recognition: 39

##  Summary

Successfully reproduced SATORI-R1 results on 2 out of 7 benchmarks from the original paper:
- **MMStar**: 55.8% vs 55.9% (paper) - General visual reasoning across 6 categories
- **OCRBench**: 764 vs ~765 (paper) - OCR and text understanding capabilities

Both results show excellent agreement with published findings, validating the model's performance.

## Experimental Setup

### Model
**SATORI-3B** - A multimodal reasoning model based on Qwen2.5-VL-3B-Instruct, trained with spatially anchored reinforcement learning for enhanced visual question answering.

### Hardware & Environment
- **Platform:** Google Colab Pro
- **GPU:** NVIDIA A100 (40GB)
- **Framework:** VLMEvalKit evaluation framework
- **Model Configuration:**
  - MAX_PIXELS: 512 × 28 × 28
  - MIN_PIXELS: 256 × 28 × 28

### Datasets Evaluated

**MMStar** (1,500 samples)
- Curated dataset of challenging multimodal questions
- Categories: Coarse Perception, Fine-grained Perception, Instance Reasoning, Logical Reasoning, Math, Science & Technology
- Evaluation time: ~3 hours

**OCRBench** (1,000 samples)
- OCR and text understanding benchmark
- Tests text recognition, document understanding, and key information extraction
- Evaluation time: ~2.5 hours

**Note on Additional Benchmarks:**
The original paper evaluated on 7 benchmarks (MMBench, MMStar, MME, OCRBench, MathVista, Math-V, MathVerse). We focused on MMStar and OCRBench due to computational constraints, as comprehensive evaluation across all benchmarks would require 30+ hours on a single GPU.

### Evaluation Procedure

The model was evaluated following the standard VQA evaluation protocol. For each sample, the model:
1. Generates an image caption describing the overall scene
2. Identifies critical regions via bounding box coordinates  
3. Produces a final answer based on spatially-grounded reasoning

Accuracy was computed by comparing model predictions against ground-truth answers, with results aggregated by category and overall performance.

## 📁 Repository Structure
```
SATORI-R1-Evaluation/
├── README.md
├── notebooks/
│   └── Satori_R1.ipynb
└── results/
    ├── MMStar_results.xlsx
    └── OCRBench_results.json
```

## 🚀 How to Run

1. **Clone the SATORI-R1 repository:**
```bash
   git clone https://github.com/justairr/SATORI-R1.git
   cd SATORI-R1
```

2. **Set up VLMEvalKit:**
```bash
   cd VLMEvalKit
   pip install -e .
```

3. **Download the model:**
   The model will be automatically downloaded from Hugging Face on first run.

4. **Run evaluation:**
```bash
   CUDA_VISIBLE_DEVICES=0 python run.py \
     --data MMStar \
     --model Qwen2.5-VL-3B-Instruct \
     --verbose
```

## 📓 Notebooks

- **[Evaluation Notebook](./Satori_R1.ipynb)** - Complete evaluation pipeline with setup and results

## 🔗 Links

- **Original Paper:** [SATORI-R1 on arXiv](https://arxiv.org/abs/2505.19094)
- **Official Repository:** [SATORI-R1 GitHub](https://github.com/justairr/SATORI-R1)
- **VLMEvalKit Framework:** [VLMEvalKit](https://github.com/open-compass/VLMEvalKit)
- **Model on Hugging Face:** [Qwen2.5-VL-3B-Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-3B-Instruct)

##  Citation

If you use this evaluation or find it helpful, please cite the original paper:
```bibtex
@article{shen2025satori,
  title={SATORI-R1: Incentivizing Multimodal Reasoning with Spatial Grounding and Verifiable Rewards},
  author={Shen, Chuming and Wei, Wei and Qu, Xiaoye and Cheng, Yu},
  journal={arXiv preprint arXiv:2505.19094},
  year={2025}
}
```

##  Acknowledgments

- Thanks to the SATORI-R1 team for their excellent paper and open-source implementation
- VLMEvalKit framework for standardized evaluation tools
- Google Colab for providing compute resources

##  Contact

For questions or issues, please open an issue in this repository.
