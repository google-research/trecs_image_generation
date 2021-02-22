# Text-to-Image Generation Grounded by Fine-Grained User Attention

This repository contains the paired word-tag data required to train a
word-to-label sequence tagger (as described in our
[paper](https://arxiv.org/abs/2011.03775)). In addition, the generated images
from the proposed TReCS model are also provided for the LN-COCO and
LN-OpenImages validation sets.

## Abstract

[Localized Narratives](https://google.github.io/localized-narratives/) is a
dataset with detailed natural language descriptions of images paired with mouse
traces that provide a sparse, fine-grained visual grounding for phrases. We
propose TReCS, a sequential model that exploits this grounding to generate
images. TReCS uses descriptions to retrieve segmentation masks and predict
object labels aligned with mouse traces. These alignments are used to select and
position masks to generate a fully covered segmentation canvas; the final image
is produced by a segmentation-to-image generator using this canvas. This
multi-step, retrieval-based approach outperforms existing direct text-to-image
generation models on both automatic metrics and human evaluations: overall, its
generated images are more photo-realistic and better match descriptions.

## Word-Tag Training Data

We release the training data used for training the sequence tagger used in
TReCS. We generate this data automatically from
[COCO-Stuff segmentation data](https://github.com/nightrome/cocostuff) and
Localized Narratives mouse traces. The full preprocessing steps are described in
Section 2.1 of our paper.

The data is available in the `sequence_labels` folder of this repository. We
provide the data for the MS-COCO split in several paired .txt files.

The lines in each set of files correspond to each other, so for example line 1
in `train_coco.ids.txt` is the ID for the first sentence in
`train_coco.words.txt`, with the tags in the first line in
`train_coco.tags.txt`.

*   `train_coco.ids.txt`: A text file where each line consists of the unique
    example IDs in the format `{image_id}_{annotator_id}` where `image_id` and
    `annotator_id` are values taken from the corresponding Localized Narratives
    examples.
*   `train_coco.words.txt`: A text file where each line consists of the
    formatted caption for the Localized Narratives. Tokens are space separated.
*   `train_coco.tags.txt`: A text file where each line consists of the processed
    labels for each word in the caption. Labels are space separated.
*   `val_coco.ids.txt`: IDs for the validation data in MS-COCO split of
    Localized Narratives.
*   `val_coco.words.txt`: Formatted caption for the validation data in the
    MS-COCO split of Localized Narratives.
*   `val_coco.tags.txt`: Labels for each word in the caption for the validation
    data in the MS-COCO split of Localized Narratives.
*   `val_oi.ids.txt`: IDs for the validation data in Open Images split of
    Localized Narratives.
*   `val_oi.words.txt`: Formatted caption for the validation data in the Open
    Images split of Localized Narratives.

## TReCS Generated Images

Our generated images can be downloaded [here](). We generate an image using the
TReCS model for each item in the Localized Narratives MS-COCO validation set.
The naming convention for the images is in the format
`{image_id}_{annotator_id}.png`, where `image_id` and `annotator_id` are values
taken from the Localized Narratives examples.

## Citation

If you find this work useful, please consider citing:

```
@inproceedings{koh2020text,
  title={Text-to-Image Generation Grounded by Fine-Grained User Attention},
  author={Koh, Jing Yu and Baldridge, Jason and Lee, Honglak and Yang, Yinfei},
  booktitle={Winter Conference on Applications of Computer Vision (WACV)},
  year={2021}
}
```

We also suggest citing the paper for the
[Localized Narratives](https://google.github.io/localized-narratives/) dataset.
The Localized Narratives dataset is licensed under CC-BY 4.0.

## Disclaimer

Not an official Google product.
