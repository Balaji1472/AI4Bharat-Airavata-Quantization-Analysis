# Airavata Model Quantization Performance Report

## Executive Summary

**Date**: 2025-07-21 13:29:08  
**Base Model**: ai4bharat/Airavata (7B parameters)  
**Test Environment**: Google Colab  
**GPU**: Tesla T4  
**Test Prompts**: 10 (Hindi and English mix)

## Key Findings


### 🏆 Best Performers
- **Fastest Model**: GGUF Quantized (23.5 tok/s)
- **Smallest Model**: GGUF Quantized (3979.2 MB)

### 📊 Performance Summary

| Model | Size (MB) | Latency (ms) | Throughput (tok/s) | GPU Memory (MB) |
|-------|-----------|--------------|-------------------|------------------|
| Original (FP16) | 13103.5 | 4202.5 | 16.0 | 13111.7 |
| 8-bit Quantized | 13103.5 | 5954.1 | 6.2 | 6940.9 |
| 4-bit Quantized | 6927.5 | 2099.0 | 12.5 | 3948.1 |
| GGUF Quantized | 3979.2 | 3407.0 | 23.5 | 0.0 |


## Detailed Analysis

### Test Configuration
- **Number of test prompts**: 10
- **Max tokens per response**: 100
- **Temperature**: 0.7
- **Repetition penalty**: 1.1

### Model Variants Tested

#### Original (FP16)
- **Model Size**: 13103.5 MB
- **Parameters**: 6870020096
- **Average Latency**: 4202.5 ms
- **Throughput**: 16.0 tokens/sec
- **GPU Memory**: 13111.7 MB

#### 8-bit Quantized
- **Model Size**: 13103.5 MB
- **Parameters**: 6870020096
- **Average Latency**: 5954.1 ms
- **Throughput**: 6.2 tokens/sec
- **GPU Memory**: 6940.9 MB

#### 4-bit Quantized
- **Model Size**: 6927.5 MB
- **Parameters**: 3632017408
- **Average Latency**: 2099.0 ms
- **Throughput**: 12.5 tokens/sec
- **GPU Memory**: 3948.1 MB

#### GGUF Quantized
- **Model Size**: 3979.2 MB
- **Parameters**: 3632017408
- **Average Latency**: 3407.0 ms
- **Throughput**: 23.5 tokens/sec
- **GPU Memory**: 0.0 MB


## Recommendations

### For Production Deployment

**4-bit Quantization** appears to offer the best balance of:
- Significant size reduction (~75%)
- Good performance maintenance
- Reasonable memory usage

**GGUF Format** is recommended for:
- CPU-only inference
- Edge deployment scenarios
- Maximum compatibility


### Next Steps
1. **Phase 2**: Implement FastAPI backend with selected quantization method
2. **Phase 3**: Test on target hardware (CPU deployment)
3. **Phase 4**: Performance optimization and final benchmarking

## Technical Notes

### Quantization Methods Tested
- **8-bit**: Uses BitsAndBytes library for 8-bit integer quantization
- **4-bit**: NF4 quantization with double quantization enabled
- **GGUF**: CPU-optimized format with various quantization levels

### Limitations
- Tests performed in Google Colab environment
- Results may vary on different hardware configurations
- Quality assessment is preliminary (manual evaluation recommended)

---

*Report generated automatically by the Airavata Model Analysis pipeline*
