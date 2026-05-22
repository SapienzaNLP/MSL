# Multilingual Semantic Layer

Welcome to the official repository for [*MSL*](https://aclanthology.org/2024.findings-acl.836/), the innovative Multilingual Semantic Layer, its Dataset and the parsing models, presented at ACL 2024.

## Features

1. **MSL dataset**: The MSL dataset provides a high-quality multilingual silver corpus in 11 languages, including Arabic, Catalan, Chinese, English, French, Galician, German, Italian, Korean, Portuguese, and Spanish. In addition, the dataset includes a manually annotated gold standard specifically designed for benchmarking and evaluation purposes.

2. **MSL parsing**: This repository extends [CLAP](https://github.com/SapienzaNLP/CLAP) by adding additional features and modifications for parsing.

If you use MSL in your research, please cite our paper:

```bibtex
@inproceedings{martinez-lorenzo-etal-2024-mitigating,
    title = "Mitigating Data Scarcity in Semantic Parsing across Languages with the Multilingual Semantic Layer and its Dataset",
    author = "Martinez Lorenzo, Abelardo Carlos  and
      Huguet Cabot, Pere-Llu{\'\i}s  and
      Ghonim, Karim  and
      Xu, Lu  and
      Choi, Hee-Soo  and
      Fern{\'a}ndez-Castro, Alberte  and
      Navigli, Roberto",
    editor = "Ku, Lun-Wei  and
      Martins, Andre  and
      Srikumar, Vivek",
    booktitle = "Findings of the Association for Computational Linguistics ACL 2024",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand and virtual meeting",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.findings-acl.836",
    doi = "10.18653/v1/2024.findings-acl.836",
    pages = "14056--14080",
}

```

## Repository Structure

- `conf/`: Configuration files for data paths, model specifications, and training parameters.
- `data/`: Datasets for benchmarking MSL evaluation.
- `experiments/`: Stores checkpoints post-training.
- `models/`: Trained Hugging Face models.
- `src/`: Source code for the project.
  - `constant.py`: Manages tokens added to the model; customizable for new tokens.
  - `linearization.py`: Implements graph linearization in Depth-First Search and compact formats.
  - `pl_data_modules.py`: Data module classes for training.
  - `pl_modules.py`: Contains new modular components for the architecture.
  - `predict.py`: Script for making predictions using trained models.
  - `predict_alignment.py`: Script for extracting alignments.
  - `predict_perplexity.py`: Script for computing perplexity.
  - `train.py`: Entry point for training models.
  - `utils.py`: Utility functions for various operations.

## Installation

```bash
# Create a Python 3.9 environment
conda create -n clap-env python=3.9
conda activate clap-env

# Install dependencies
pip install -r requirements.txt
```


## Training 

Configure paths and hyperparameters in conf/ directory files:

- conf/data.yaml: Specify dataset paths for training and evaluation.
- conf/model.yaml: Define the model architecture, e.g., google/flan-t5-small.
- conf/train.yaml: Adjust training-specific hyperparameters.

```bash
python src/train.py
```

## Prediction

Set up the necessary paths in conf/data.yaml and conf/model.yaml. Then run:

```bash
python src/predict.py
```

# Alignment Extraction

Configure as per the prediction step and execute:

```bash
python src/predict_alignments.py
```

# Perplexity Calculation

Configure as per the prediction step and execute:

```bash
python src/predict_perplexity.py
```

## License
This project is released under the CC-BY-NC-SA 4.0 license (see `LICENSE`). If you use AMRs-Assemble!, please reference the paper and put a link to this repo.

## Contributing

We welcome contributions to the Cross-lingual AMR Aligner project. If you have any ideas, bug fixes, or improvements, feel free to open an issue or submit a pull request.

## Contact

For any questions or inquiries, please contact Roberto Navigli at navigli@diag.uniroma.it
