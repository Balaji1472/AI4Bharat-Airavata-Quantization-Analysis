# FINAL BENCHMARK REPORT

---

## DETAILED PERFORMANCE METRICS:

| model  | time_to_first_token_mean | time_to_first_token_std | total_latency_mean | total_latency_std | throughput_mean | throughput_std | file_size_mb_first |
|--------|---------------------------|--------------------------|---------------------|--------------------|------------------|------------------|---------------------|
| Q2_K   | 0.4379                    | 0.1461                   | 1.5877              | 1.3959             | 12.2036          | 7.0295           | 2488.1201           |
| Q4_K_M | 0.5029                    | 0.1683                   | 2.5256              | 1.5628             | 12.8943          | 8.6462           | 3979.2499           |
| Q6_K   | 0.4640                    | 0.1507                   | 2.9929              | 2.0739             | 10.5276          | 7.5846           | 5376.5302           |

---

## PERFORMANCE RANKING:

1. FASTEST FIRST TOKEN: Q2_K (0.438s)  
2. LOWEST LATENCY: Q2_K (1.59s)  
3. HIGHEST THROUGHPUT: Q4_K_M (12.9 tokens/s)  
4. SMALLEST SIZE: Q2_K (2488 MB)

---

## RECOMMENDATION:

**BEST OVERALL MODEL: Q4_K_M**
- Throughput: 12.9 tokens/s  
- Latency: 2.53s  
- First Token: 0.503s  
- Size: 3979 MB

**MOST EFFICIENT MODEL: Q2_K**
- Efficiency Score: 0.005 tokens/s/MB

**SMALLEST MODEL: Q2_K**
- Good for resource-constrained environments
