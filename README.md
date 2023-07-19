# CLIP Score for PyTorch

[![PyPI](https://img.shields.io/pypi/v/clip-score.svg)](https://pypi.org/project/clip-score/)

This repository provides a batch-wise quick processing for calculating CLIP scores. It uses the pretrained CLIP model to measure the cosine similarity between two modalities. The project structure is adapted from [pytorch-fid](https://github.com/mseitzer/pytorch-fid) and [CLIP](https://github.com/openai/CLIP).

## Installation

Requirements:
- Install PyTorch:
  ```
  pip install torch  # Choose a version that suits your GPU
  ```
- Install CLIP:
  ```
  pip install git+https://github.com/openai/CLIP.git
  ```
- Install clip-score from [PyPI](https://pypi.org/project/clip-score/):
  ```
  pip install clip-score
  ```

## Usage

To compute the CLIP score between images and texts, make sure that the image and text data are contained in two separate folders, and each sample has the same name in both modalities. Run the following command:
```
python -m clip_score path/to/image path/to/text
```

To run the evaluation on a GPU, use the `--device cuda:N` flag, where `N` is the index of the GPU to use.

## Computing CLIP Score within the Same Modality

If you want to calculate the CLIP score within the same modality (e.g., image-image or text-text), follow the same folder structure as mentioned above. Additionally, specify the preferred modalities using the `--real_flag` and `--fake_flag` options. By default, `--real_flag=img` and `--fake_flag=txt`. Examples:
```
python -m clip_score path/to/imageA path/to/imageB --real_flag img --fake_flag img
python -m clip_score path/to/textA path/to/textB --real_flag txt --fake_flag txt
```

## Citing

If you use this repository in your research, consider citing it using the following Bibtex entry:

```
@misc{taited2023CLIPScore,
  author={SUN Zhengwentai},
  title={{clip-score: CLIP Score for PyTorch}},
  month={March},
  year={2023},
  note={Version 0.1.0},
  howpublished={\url{https://github.com/taited/clip-score}},
}
```

## License

This implementation is licensed under the Apache License 2.0.

The project structure is adapted from [mseitzer's pytorch-fid](https://github.com/mseitzer/pytorch-fid) project. The CLIP model is adapted from [OpenAI's CLIP](https://github.com/openai/CLIP).

The CLIP Score was introduced in OpenAI's [Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/abs/2103.00020).
