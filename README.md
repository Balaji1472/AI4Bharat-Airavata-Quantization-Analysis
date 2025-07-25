# Airavata Model Quantization Performance Analysis

## Overview

Comprehensive performance benchmarking of ai4bharat/Airavata (7B parameters) across different quantization methods using Google Colab with Tesla T4 GPU. This analysis led to the development of a production-ready FastAPI chat application using the optimized GGUF quantized model.

## Key Results

### Performance Rankings (Initial Analysis)

🏆 **GGUF Quantized**: Highest throughput (23.5 tok/s), smallest size (3.98 GB) 
🥈 **Original FP16**: Balanced performance (16.0 tok/s), largest size (13.1 GB)
🥉 **4-bit Quantized**: Good efficiency (12.5 tok/s), moderate size (6.93 GB)
🚫 **8-bit Quantized**: Lowest throughput (6.2 tok/s), same size as original

### Quantization Impact Summary

| Model | Size Reduction | Speed Change | Memory Savings | Production Ready   |
| ----- | -------------- | ------------ | -------------- | ------------------ |
| 4-bit | -47%           | -22%         | -70%           | ✅ GPU Deploy       |
| 8-bit | 0%             | -61%         | -47%           | ❌ Poor Performance |
| GGUF  | -70%           | +47%         | -100%\*        | ✅ CPU Deploy       |

\*GGUF runs on CPU, hence 0 GPU memory usage

---

## Revised Analysis: Q2, Q4, and Q6 GGUF Quantization

To further optimize model efficiency, a detailed benchmark of **three GGUF quantized variants** (Q2\_K, Q4\_K\_M, Q6\_K) was conducted on **Google Colab (Tesla T4 GPU)**. The revised results provided a clearer tradeoff between model size, latency, and throughput.

### Revised Benchmark Results (GGUF Models)

| Model    | First Token Latency (s) | Total Latency (s) | Throughput (tok/s) | Size (MB) |
| -------- | ----------------------- | ----------------- | ------------------ | --------- |
| Q2\_K    | 0.389                   | 2.078             | 13.04              | 2488.12   |
| Q4\_K\_M | 0.426                   | 2.074             | **14.03**          | 3979.25   |
| Q6\_K    | **0.383**               | 2.372             | 10.39              | 5376.53   |

### Observations:

* **Q4\_K\_M** had the highest throughput (14.03 tok/s), balancing speed and size.
* **Q2\_K** had the lowest latency but slightly less throughput.
* **Q6\_K** had higher latency and larger size without performance gains.

### Files Added for Revised Analysis

* 📊 `revised_analysis_results/revised_model_efficiency_chart.png`
* 📊 `revised_analysis_results/revised_performance_comparison_chart.png`
* 📄 `revised_analysis_results/benchmark_results.csv`

These results help validate Q4\_K\_M as the **ideal GGUF variant for deployment**, especially in constrained environments.

---

## Recommendations

### ✅ Production Deployment

* **GGUF Format** (Q4\_K\_M): CHOSEN for production chat app – ideal for CPU deployment, edge devices, and cost-effective scaling
* **4-bit Quantization**: Good alternative for GPU-based deployments needing faster generation

### ❌ Avoid

* **8-bit Quantization**: Poor performance with no storage benefit
* **Original FP16**: Too large and resource-intensive

## Technical Implementation

* **Test Environment**: Google Colab, Tesla T4 GPU
* **Benchmark Dataset**: 10 Hindi/English prompts, 100 max tokens each
* **Quantization Libraries**: BitsAndBytes (4/8-bit), llama-cpp-python (GGUF)
* **Model Source**: ai4bharat/Airavata 7B

## Repository Structure

```
├── README.md
├── docs/
│   └── airavata_quantization_report.md
├── data/
│   └── benchmark_results.json
├── visualizations/
│   ├── model_efficiency_chart.png
│   └── performance_comparison_chart.png
├── revised_analysis_results/
│   ├── revised_model_efficiency_chart.png
│   ├── revised_performance_comparison_chart.png
│   ├── final_report.md
│   └── benchmark_results.csv
├── notebooks/
│   ├── airavata_quantization_benchmark.ipynb
│   └── Revised_model_optimization_analysis.ipynb
├── requirements.txt
└── LICENSE
```

---

## Production Implementation

Based on this quantization analysis, we implemented a FastAPI-based chat application using the **GGUF Q4\_K\_M** model for optimal performance and resource efficiency.

### 🚀 Chat Application: BharatChat-AI

An Indian LLM-powered chat assistant built using the optimized GGUF model.

GitHub Repo: `Balaji1472/BharatChat-AI`

### Features Enabled by GGUF Quantization:

* Lightweight Deployment (3.98GB)
* CPU-Only Inference
* Real-time Responses (\~23.5 tok/s)
* Multilingual Support
* FastAPI-Based Backend for Scalability

---

## Results Impact

This analysis informed a practical and deployable solution using **Q4\_K\_M GGUF**, balancing size, speed, and cost-efficiency. It enabled real-world applications on edge and CPU environments without sacrificing usability or user experience.

**Analysis completed on July 21, 2025 | Environment: Google Colab | GPU: Tesla T4**
