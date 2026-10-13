# GAINER: Gain-Aware Allocation of Transformer Depth for Efficient Cross-Encoder Re-Ranking

This repository contains the code and the registered runs of the paper

> I. Mohd Jamadi and S. Anuar, "GAINER: Gain-Aware Allocation of Transformer Depth for Efficient Cross-Encoder Re-Ranking," preprint, 2026. Submitted to the International Journal of Advanced Computer Science and Applications (IJACSA).

GAINER (Gain-Aware Allocation for Neural Re-ranking) treats a block of cross-encoder layers as a unit of computation that can be spent on any active candidate. At each intermediate checkpoint, small rankers trained on counterfactual nDCG@10 gains order the active candidates, and an exact-budget schedule decides how many advance. A leak test verifies that every allocation decision uses only computation that has already been paid for, and latency is measured with true conditional execution.

## Contents

| Path | Description |
|---|---|
| `GAINER_v3.ipynb` | Google Colab notebook of the main registered run (hypotheses H1–H3): BEIR data and BM25 pools, trajectory extraction for both backbones, exit heads, the GAINER controller, all baselines (Current Rank, Boundary, Random, Fixed depth, FixedResidual, Patience, SEE, Oracle), the leave-one-dataset-out driver, measured latency, statistics, tables and figures. Saved with the outputs of the registered run. |
| `GAINER_v3_1.ipynb` | Notebook of the second registered family (H4–H6): calibrated uncertainty heads and the label-free value-of-computation (VOC) rule. It reads the cached data of the v3 run. Saved with the outputs of the registered run. |
| `results/` | Pre-registration files, per-query results and tables of the two runs (added with the first tagged release). |
| `requirements.txt` | Package versions of the registered runs |

## Pre-registration

| Run | Pre-registration file | SHA-256 |
|---|---|---|
| v3 (H1–H3) | `results/v3/preregistration_v3.json` | `e77241073ba22c17b36151adcffacaf3e7f47ff36b3fd38cbebae413026b4746` |
| v3.1 (H4–H6) | `results/v3_1/preregistration_v3_1.json` | `1f4050281d4dbf8a27543aa6672f7295ea86880db50d1aecea2818ec52ef11b1` |

Each notebook writes its pre-registration file before any of its results exist and stops if the registered settings are changed afterwards.

## Reproducing the results

1. Open `GAINER_v3.ipynb` in Google Colab with a GPU runtime and run all cells. The BEIR datasets (ArguAna, FiQA-2018, NFCorpus, SCIDOCS, SciFact, TREC-COVID and Touché-2020) are downloaded from their public releases, and every stage is cached in Google Drive, so an interrupted run resumes where it stopped.
2. Then run `GAINER_v3_1.ipynb`, which reuses the cached pools and trajectories of the v3 run.

Setting `QUICK_TRIAL = True` in the configuration cell runs an end-to-end check on two datasets with one seed, written to separate folders.

## Use in later work

The same implementation is used without modification, with a multilingual data layout and a leave-one-language-out driver, in [SEAFact-Bench](https://github.com/ibrahimjamadi98/SEAFact-Bench).

## Citation

```bibtex
@misc{mohdjamadi2026gainer,
  author = {Mohd Jamadi, Ibrahim and Anuar, Syahid},
  title  = {{GAINER}: Gain-Aware Allocation of {T}ransformer Depth for Efficient Cross-Encoder Re-Ranking},
  note   = {Preprint. Submitted to the International Journal of Advanced Computer Science and Applications},
  year   = {2026}
}
```

## Contact

Ibrahim Mohd Jamadi, Faculty of Artificial Intelligence, Universiti Teknologi Malaysia (ibrahim98@graduate.utm.my).

## License

The code is released under the MIT License (see `LICENSE`). Each dataset keeps the licence and terms of its original release.
