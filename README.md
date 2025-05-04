# Vietnamese NER Fine-tuning with PhoBERT

This repository contains two Jupyter Notebooks for fine-tuning [PhoBERT](https://huggingface.co/VinAI/phobert-base) on the task of Named Entity Recognition (NER) in Vietnamese.

## Contents

- `NER_PhoBert.ipynb`: Data preprocessing, dataset preparation, and model setup using PhoBERT for NER.
- `finetune_roBerta_final.ipynb`: Fine-tuning and evaluation notebook based on RoBERTa (PhoBERT).

## Requirements

Install the necessary dependencies via:

```bash
pip install transformers seqeval underthesea scikit-learn
```

Note: PhoBERT requires Vietnamese tokenization using `underthesea` or `VnCoreNLP`.

## Model

- Pretrained model: `VinAI/phobert-base`
- Fine-tuning: Token classification for NER using HuggingFace `transformers`.

## Citation

If you use PhoBERT, please cite:

```
@inproceedings{nguyen2020phobert,
  title={PhoBERT: Pre-trained language models for Vietnamese},
  author={Nguyen, Dat Quoc and Nguyen, Anh Tuan},
  booktitle={Findings of EMNLP},
  year={2020}
}
```

## License

MIT License.
