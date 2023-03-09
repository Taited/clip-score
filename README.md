[![PyPI](https://img.shields.io/pypi/v/clip-score.svg)](https://pypi.org/project/clip-score/)

# CLIP score for PyTorch

This repository provides a batch-wise quick processing for calculating CLIP scores. 
The project structure is adapted from (pytorch-fid)[https://github.com/mseitzer/pytorch-fid] and (CLIP)[https://github.com/openai/CLIP].

The CLIP Score measures the Cosine Similarity between two embedded features.
This repository utilizes the pretrained (CLIP Model)[https://github.com/openai/CLIP] to calculate 
the mean average of cosine similarities between two modalities.

## Installation

Install from [pip](https://pypi.org/project/clip-score/):

```
pip install clip-score
```

Requirements:
- python3
- pytorch
- torchvision
- pillow
- numpy

## Usage

We assume that the image and the text data are contained in two individual folders. What's more, there is the same name of each sample in two modalities. To compute the CLIP score between images and texts:
```
python -m clip_score path/to/image path/to/text
```

To run the evaluation on GPU, use the flag `--device cuda:N`, where `N` is the index of the GPU to use.

## To measure the CLIP Score within image-image or text-text:
In case you would like to calculate the CLIP score in the same modality, the folder structure
should follow the upper usage case. Besides, you need to specify the prefered modalities by 
`--real_flag` and `--fake_flag`. `--real_flag` refers to the modality of the former path and the `--fake_flag` refers to the later. The default settins are `--real_flag=img` and `--fake_flag=txt`.
For example:
```
python -m clip_score path/to/imageA path/to/imageB --real_flag img --fake_flag img
python -m clip_score path/to/textA path/to/textB --real_flag txt --fake_flag txt
```

## Citing

If you use this repository in your research, consider citing it using the following Bibtex entry:

```
@misc{taited2023CLIPScore,
  author={SUN Zhengwentai},
  title={{clip-score: FID Score for PyTorch}},
  month={March},
  year={2023},
  note={Version 0.1.0},
  howpublished={\url{https://github.com/taited/clip-score}},
}
```

## License

This implementation is licensed under the Apache License 2.0.

The project structure is adapted from [mseitzer's pytorch-fid](https://github.com/mseitzer/pytorch-fid) project. The CLIP model is adapted from [OpenAI's CLIP](https://github.com/openai/CLIP).

The CLIP Score was introduced in OpenAI's [Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/abs/2103.00020)
