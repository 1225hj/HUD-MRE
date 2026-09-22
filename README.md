# HUD-MRE
This repository implements the **HUD-MRE** multimodal relation extraction framework, which is developed and improved based on the open-source code of the FocalMRE baseline model.Two core modules, uncertainty-driven semantic alignment and evidence-aware cross-modal fusion, are proposed to mitigate multimodal noise interference and boost extraction performance on the public MNRE benchmark and the self-built agricultural disease dataset AgDi-MRE.

## Citation Requirement
If you adopt this source code or the UDSE-MRE method in your research publications, you are required to cite both this work and the original FocalMRE baseline paper.
```bibtex
@inproceedings{udse_mre,
  title={UDSE-MRE: Uncertainty-Driven Semantic Alignment with Evidence Fusion for Agricultural Multimodal Relation Extraction},
}

@inproceedings{Focalmre,
  title={Focus \& Gating: A Multimodal approach for unveiling relations in noisy social media},
  author={He, Liang and Wang, Hongke and Wu, Zhen and Zhang, Jianbing and Dai, Xinyu and Chen, Jiajun},
  booktitle={Proceedings of the 32nd ACM International Conference on Multimedia},
  pages={1379--1388},
  year={2024}
}
```

## Data preprocessing
### MNRE dataset
The MNRE dataset occupies large storage space. Download the original dataset resources from the official open repository: 
Extract the compressed data files and place all data contents into the `data` folder under the project root path.

Create an empty directory to store model checkpoint files:
```shell
mkdir ckpt
```
The pre-computed visual object features inherited from the baseline work can be downloaded and decompressed via the following commands:
```shell
cd data/
wget 120.27.214.45/Data/re/multimodal/data.tar.gz
tar -xzvf data.tar.gz
```

### AgDi-MRE dataset
AgDi-MRE is a domain-specific multimodal relation extraction dataset focusing on agricultural diseases. This dataset is independently constructed for this research and cannot be publicly released due to project confidentiality constraints. Relevant access permission can be applied by contacting the corresponding author for academic communication purposes.

## Dependencies
Build the running environment and install all required dependent packages with the given command lines:
```shell
conda create -n udse_mre python==3.7
conda activate udse_mre
pip install -r requirements.txt
```

## Model Training
All optimized hyperparameters for UDSE-MRE are pre-configured within the `run_mre.sh` script file.
Execute the script directly to launch the multimodal relation extraction training process:
```shell
sh run_mre.sh
```
The model checkpoint with the best validation F1 score will be automatically saved into the `ckpt` folder during the whole training process.

## Model Testing
Run the test script to evaluate model performance using saved checkpoint files:
```shell
sh run_test.sh
```

## Acknowledgements
The implementation of this code heavily relies on the open-source project of FocalMRE. We express sincere gratitude to the original contributors for publishing source code and processed multimodal data, which strongly supports the algorithm optimization and experimental verification of this work.
