# Airavata Model Quantization Performance Analysis

## Overview
Comprehensive performance benchmarking of ai4bharat/Airavata (7B parameters) across different quantization methods using Google Colab with Tesla T4 GPU. This analysis led to the development of a production-ready FastAPI chat application using the optimized GGUF quantized model.

## Key Results

### Performance Rankings
1. **🏆 GGUF Quantized**: Highest throughput (23.5 tok/s), smallest size (3.98 GB) ⭐ **WINNER**
2. **🥈 Original FP16**: Balanced performance (16.0 tok/s), largest size (13.1 GB)  
3. **🥉 4-bit Quantized**: Good efficiency (12.5 tok/s), moderate size (6.93 GB)
4. **8-bit Quantized**: Lowest throughput (6.2 tok/s), same size as original

### Quantization Impact Summary
| Model | Size Reduction | Speed Change | Memory Savings | Production Ready |
|-------|---------------|--------------|----------------|------------------|
| 4-bit | **-47%** | -22% | **-70%** | ✅ GPU Deploy |
| 8-bit | 0% | **-61%** | -47% | ❌ Poor Performance |
| GGUF | **-70%** | **+47%** | **-100%*** | ✅ CPU Deploy |

*GGUF runs on CPU, hence 0 GPU memory usage

## Model Performance Comparison

### Size vs Throughput Analysis
- **GGUF Quantized** achieves the best efficiency ratio: smallest size with highest speed
- **70% size reduction** compared to original model (13.1GB → 3.98GB)
- **47% speed improvement** making it ideal for real-time applications
- **Zero GPU memory usage** enables deployment on CPU-only servers

### Latency Comparison
- Original (FP16): 4,202ms average latency
- GGUF Quantized: 3,407ms average latency (**19% faster**)
- 4-bit Quantized: 2,099ms average latency (fastest GPU option)

## Recommendations

### ✅ Production Deployment
- **GGUF Format**: **CHOSEN** for production chat app - ideal for CPU deployment, edge devices, and cost-effective scaling
- **4-bit Quantization**: Alternative for GPU-based deployments requiring maximum speed

### ❌ Avoid
- **8-bit Quantization**: Poor performance with no size benefits
- **Original FP16**: Too large for efficient deployment

## Technical Implementation
- **Test Environment**: Google Colab, Tesla T4 GPU
- **Benchmark Dataset**: 10 Hindi/English prompts, 100 max tokens each
- **Quantization Libraries**: BitsAndBytes (4/8-bit), llama-cpp-python (GGUF)
- **Model Source**: ai4bharat/Airavata 7B parameter model

## Repository Structure
```
├── README.md                          # This file
├── docs/
│   ├── airavata_quantization_report.md    # Detailed analysis report
├── data/
│   └── benchmark_results.json             # Raw performance data
├── visualizations/
│   ├── model_efficiency_chart.png         # Size vs Throughput visualization
│   └── performance_comparison_chart.png   # Multi-metric comparison
├── notebooks/
│   └── airavata_quantization_benchmark.ipynb
├── requirements.txt                       # Dependencies
└── LICENSE
```

## Production Implementation

Based on this quantization analysis, we implemented a **FastAPI-based chat application** using the **GGUF quantized model** for optimal performance and resource efficiency.

### 🚀 Chat Application
**BharatChat-AI** - An Indian LLM-Powered Chat Assistant built using the optimized GGUF model from this analysis.

**Repository**: [Balaji1472/BharatChat-AI: An Indian LLM-Powered Chat Assistant Using AI4Bharat's Airavata Model](https://github.com/Balaji1472/BharatChat-AI)

### Features Enabled by GGUF Quantization:
- **Lightweight Deployment**: 3.98GB model size enables easy hosting
- **CPU-Only Operation**: No GPU requirements, reducing infrastructure costs  
- **Fast Response Times**: 23.5 tokens/second for real-time chat experience
- **Multilingual Support**: Optimized for Hindi and English conversations
- **Scalable Architecture**: FastAPI backend supports multiple concurrent users

## Results Impact
This quantization analysis directly informed the production deployment strategy, with **GGUF quantization** proving to be the optimal choice for building a responsive, cost-effective chat application that maintains model quality while dramatically reducing resource requirements.

---
*Analysis conducted on July 21, 2025 | Tesla T4 GPU | Google Colab*
*Production deployment: BharatChat-AI FastAPI Application*