# AdParaphrase

This repository contains data for our paper "AdParaphrase: Paraphrase Dataset for Analyzing Linguistic Features toward Generating Attractive Ad Texts" (NAACL2025 Findings).

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

@inproceedings{murakami-etal-2025-adparaphrase,
    title = "{A}d{P}araphrase: Paraphrase Dataset for Analyzing Linguistic Features toward Generating Attractive Ad Texts",
    author = "Murakami, Soichiro  and
      Zhang, Peinan  and
      Kamigaito, Hidetaka  and
      Takamura, Hiroya  and
      Okumura, Manabu",
    editor = "Chiruzzo, Luis  and
      Ritter, Alan  and
      Wang, Lu",
    booktitle = "Findings of the Association for Computational Linguistics: NAACL 2025",
    month = apr,
    year = "2025",
    address = "Albuquerque, New Mexico",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.findings-naacl.78/",
    pages = "1426--1439",
    ISBN = "979-8-89176-195-7",
    abstract = "Effective linguistic choices that attract potential customers play crucial roles in advertising success. This study aims to explore the linguistic features of ad texts that influence human preferences. Although the creation of attractive ad texts is an active area of research, progress in understanding the specific linguistic features that affect attractiveness is hindered by several obstacles. First, human preferences are complex and influenced by multiple factors, including their content, such as brand names, and their linguistic styles, making analysis challenging. Second, publicly available ad text datasets that include human preferences are lacking, such as ad performance metrics and human feedback, which reflect people`s interests. To address these problems, we present AdParaphrase, a paraphrase dataset that contains human preferences for pairs of ad texts that are semantically equivalent but differ in terms of wording and style. This dataset allows for preference analysis that focuses on the differences in linguistic features. Our analysis revealed that ad texts preferred by human judges have higher fluency, longer length, more nouns, and use of bracket symbols. Furthermore, we demonstrate that an ad text-generation model that considers these findings significantly improves the attractiveness of a given text. The dataset is publicly available at: https://github.com/CyberAgentAILab/AdParaphrase."
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
@inproceedings{zhang-etal-2025-adtec,
    title = "{A}d{TEC}: A Unified Benchmark for Evaluating Text Quality in Search Engine Advertising",
    author = "Zhang, Peinan  and
      Sakai, Yusuke  and
      Mita, Masato  and
      Ouchi, Hiroki  and
      Watanabe, Taro",
    editor = "Chiruzzo, Luis  and
      Ritter, Alan  and
      Wang, Lu",
    booktitle = "Proceedings of the 2025 Conference of the Nations of the Americas Chapter of the Association for Computational Linguistics: Human Language Technologies (Volume 1: Long Papers)",
    month = apr,
    year = "2025",
    address = "Albuquerque, New Mexico",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.naacl-long.391/",
    pages = "7672--7691",
    ISBN = "979-8-89176-189-6",
    abstract = "As the fluency of ad texts automatically generated by natural language generation technologies continues to improve, there is an increasing demand to assess the quality of these creatives in real-world setting.We propose **AdTEC**, the first public benchmark to evaluate ad texts from multiple perspectives within practical advertising operations.Our contributions are as follows: (i) Defining five tasks for evaluating the quality of ad texts, as well as constructing a Japanese dataset based on the practical operational experiences of advertising agencies, which are typically maintained in-house. (ii) Validating the performance of existing pre-trained language models (PLMs) and human evaluators on this dataset. (iii) Analyzing the characteristics and providing challenges of the benchmark.Our results show that while PLMs have a practical level of performance in several tasks, humans continue to outperform them in certain domains, indicating that there remains significant potential for further improvement in this area."
}
```

## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><span property="dct:title">AdParaphrase</span> is licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY-NC-SA 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1" alt=""></a></p>
