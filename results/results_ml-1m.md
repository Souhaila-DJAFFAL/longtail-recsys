### Test results (ml-1m, full ranking, K=10)

| model      |   HR@10 |   NDCG@10 |   NDCG@10 head |   NDCG@10 tail |   Coverage@10 |   TailShare@10 |    ARP@10 |
|:-----------|--------:|----------:|---------------:|---------------:|--------------:|---------------:|----------:|
| Popularity |  0.0369 |    0.0180 |         0.0309 |         0.0000 |        0.0583 |         0.0000 | 2513.7842 |
| BPR-MF     |  0.0801 |    0.0399 |         0.0616 |         0.0095 |        0.5597 |         0.1123 | 1352.8610 |
| SASRec     |  0.2459 |    0.1315 |         0.1739 |         0.0721 |        0.6964 |         0.2776 |  925.9801 |

### Popularity-aware re-ranking

| model   |   lambda |   NDCG@10 |   NDCG@10 tail |   Coverage@10 |   TailShare@10 |    ARP@10 |
|:--------|---------:|----------:|---------------:|--------------:|---------------:|----------:|
| BPR-MF  |   0.0000 |    0.0399 |         0.0095 |        0.5597 |         0.1123 | 1352.8610 |
| BPR-MF  |   0.1000 |    0.0403 |         0.0108 |        0.5978 |         0.1385 | 1288.0083 |
| BPR-MF  |   0.2500 |    0.0393 |         0.0127 |        0.6622 |         0.1868 | 1184.1492 |
| BPR-MF  |   0.5000 |    0.0370 |         0.0173 |        0.7939 |         0.2973 |  990.5878 |
| BPR-MF  |   0.7500 |    0.0332 |         0.0217 |        0.9330 |         0.4519 |  767.3625 |
| BPR-MF  |   1.0000 |    0.0237 |         0.0226 |        0.9939 |         0.6873 |  450.2457 |
| SASRec  |   0.0000 |    0.1315 |         0.0721 |        0.6964 |         0.2776 |  925.9801 |
| SASRec  |   0.1000 |    0.1259 |         0.0819 |        0.7725 |         0.3552 |  808.7426 |
| SASRec  |   0.2500 |    0.1112 |         0.0904 |        0.8809 |         0.5114 |  611.6553 |
| SASRec  |   0.5000 |    0.0604 |         0.0756 |        0.9356 |         0.8318 |  249.0587 |
| SASRec  |   0.7500 |    0.0216 |         0.0438 |        0.7108 |         0.9877 |   58.1973 |
| SASRec  |   1.0000 |    0.0094 |         0.0223 |        0.4479 |         0.9998 |   25.0156 |

### Key findings

- SASRec reaches NDCG@10 = 0.1315, +229.7% vs. BPR-MF and +629.1% vs. Popularity.
- For users whose target is a tail item, NDCG@10 is 0.0721 (SASRec) and 0.0095 (BPR-MF), against 0.1739 and 0.0616 for head targets.
- Tail items make up 27.8% (SASRec) and 11.2% (BPR-MF) of top-10 lists; catalogue coverage is 69.6% and 56.0%.
- BPR-MF re-ranked with λ = 0.25 keeps ≥95% of its NDCG@10 (0.0393 vs. 0.0399) while tail share goes from 11.2% to 18.7% and coverage from 56.0% to 66.2%.
- SASRec re-ranked with λ = 0.1 keeps ≥95% of its NDCG@10 (0.1259 vs. 0.1315) while tail share goes from 27.8% to 35.5% and coverage from 69.6% to 77.3%.
