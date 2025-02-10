# AdParaphrase

This repository contains data for our paper "AdParaphrase: Paraphrase Dataset for Analyzing Linguistic Features toward Generating Attractive Ad Texts".

## Overview

AdParaphrase is a novel paraphrase dataset that contains human preferences for pairs of ad texts that are semantically equivalent but differ in wording and style. We carefully constructed the dataset by collecting semantically similar ad texts, performing paraphrase identification with five judges per pair, and collecting human preference judgments with ten judges per pair. The dataset allows us to focus on differences in linguistic features between individual ad texts while minimizing the impact of differences in semantic content. Thus, we can analyze human preferences centered on these features.

## File format

The AdParaphrase dataset is stored in [data/adparaphrase.csv](data/adparaphrase.csv). The file contains the following columns:

- `index`
  - Index of ad text pair
- `ad1`
  - ad1 is the source ad text for paraphrase candidate generation, which is originally from the AdSimilarity or CAMERA dataset.
- `ad2`
  - ad2 is an ad text extracted from AdSimilarity or a generated ad text by LLMs or human experts based on ad1. See source_ad2 for details.
- `source_ad1`
  - Source of ad1. This can be `adsimilarity` or `camera`.
- `source_ad2`
  - Source of ad2. This can be `adsimilarity` or a model (`human`, `llama2`, `gpt35`, or `gpt4`) that generated ad2 from ad1.
- `count.nonparaphrase`
  - Number of judges who labeled an ad text pair (ad1, ad2) as non-paraphrases in paraphrase identification
- `count.paraphrase`
  - Number of judges who labeled an ad text pair (ad1, ad2) as paraphrases in paraphrase identification
- `count.preference_skip`
  - Number of judges who skipped an ad text pair (ad1, ad2) in attractiveness evaluation
- `count.preference_ad1`
  - Number of judges who preferred ad1 over ad2
- `count.preference_ad2`
  - Number of judges who preferred ad2 over ad1

**Note**

- Because we performed human preference judgments on paraphrased ad text pairs, nonparaphrased pairs do not contain the results of preference judgments. Specifically, we set `count.prefenence_{skip,ad1,ad2}` to 0 when a majority of judges (three or more judges out of five judges) labeled ad text pairs as nonparaphrases.

## Citation

If you use AdParaphrase, please cite our paper:

```bibtex
@misc{murakami2025adparaphrase,
      title={AdParaphrase: Paraphrase Dataset for Analyzing Linguistic Features toward Generating Attractive Ad Texts},
      author={Soichiro Murakami and Peinan Zhang and Hidetaka Kamigaito and Hiroya Takamura and Manabu Okumura},
      year={2025},
      eprint={2502.04674},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2502.04674},
}
```

## References

AdParaphrase is built upon the following two datasets, [CAMERA](https://aclanthology.org/2024.acl-long.54/) and [AdSimilarity](https://arxiv.org/abs/2408.05906):

```bibtex
# CAMERA
@inproceedings{mita-etal-2024-striking,
    title = "Striking Gold in Advertising: Standardization and Exploration of Ad Text Generation",
    author = "Mita, Masato  and
      Murakami, Soichiro  and
      Kato, Akihiko  and
      Zhang, Peinan",
    editor = "Ku, Lun-Wei  and
      Martins, Andre  and
      Srikumar, Vivek",
    booktitle = "Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.acl-long.54/",
    doi = "10.18653/v1/2024.acl-long.54",
    pages = "955--972",
    abstract = "In response to the limitations of manual ad creation, significant research has been conducted in the field of automatic ad text generation (ATG). However, the lack of comprehensive benchmarks and well-defined problem sets has made comparing different methods challenging. To tackle these challenges, we standardize the task of ATG and propose a first benchmark dataset, CAMERA, carefully designed and enabling the utilization of multi-modal information and facilitating industry-wise evaluations. Our extensive experiments with a variety of nine baselines, from classical methods to state-of-the-art models including large language models (LLMs), show the current state and the remaining challenges. We also explore how existing metrics in ATG and an LLM-based evaluator align with human evaluations."
}

# AdSimilarity (contained in AdTEC Benchmark)
@misc{zhang2024adtecunifiedbenchmarkevaluating,
      title={AdTEC: A Unified Benchmark for Evaluating Text Quality in Search Engine Advertising},
      author={Peinan Zhang and Yusuke Sakai and Masato Mita and Hiroki Ouchi and Taro Watanabe},
      year={2024},
      eprint={2408.05906},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2408.05906},
}
```

## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><span property="dct:title">AdParaphrase</span> is licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY-NC-SA 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1" alt=""></a></p>
