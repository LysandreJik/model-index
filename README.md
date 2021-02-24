# model-index: maintain a source of truth for ML models

<p align="center">
[![paperswithcode](https://circleci.com/gh/paperswithcode/model-index.svg?style=svg)](https://app.circleci.com/pipelines/github/paperswithcode/model-index)
</p>

`model-index` has two goals:
- Make it easy to maintain a source-of-truth index of Machine Learning model metadata 
- Enable the community browse this model metadata on [Papers with Code](https://paperswithcode.com/)

The main design principle of `model-index` is **flexibility**. You can store your model metadata however is the
most convenient for you - as JSONs, YAMLs or as annotations inside markdown. `model-index` provides a convenient
way to collect all this metadata into a single file that's browsable, searchable and comparable.

You can use this library locally or choose to upload the metadata to [Papers with Code](https://paperswithcode.com)
to have your library featured on the website. 

## How it works

There is a root file for the model index: `model-index.yml` that links to (or contains) metadata. 

```yaml
Models:
  - Name: Inception v3
    Metadata:
      FLOPs: 11462568384
      Parameters: 23834568
      Epochs: 90
      Batch Size: 32
      Training Data: ImageNet  
      Training Techniques: 
        - RMSProp
        - Weight Decay
        - Gradient Clipping
        - Label Smoothing
      Training Resources: 8x V100 GPUs
      Architecture:
        - Auxiliary Classifier
        - Inception-v3 Module
    Results:
      - Task: Image Classification
        Dataset: ImageNet
        Metrics:
          Top 1 Accuracy: 74.67%
          Top 5 Accuracy: 92.1%
    Paper: https://arxiv.org/abs/1512.00567v3
    Code: https://github.com/rwightman/pytorch-image-models/blob/timm/models/inception_v3.py#L442
    Weights: https://download.pytorch.org/models/inception_v3_google-1a9a5a14.pth 
    README: docs/inception-v3-readme.md
```

You can add any fields you like, but the ones above have a standard meaning across different models and libraries. 

### Storing metadata in markdown files

Metadata can also be directly stored in model's README file. For example in this `docs/rexnet.md` file:

```markdown
<!--
Type: model-index
Name: RexNet
Metadata: 
  Epochs: 400
  Batch Size: 512
Paper: https://arxiv.org/abs/2007.00992v1
-->

# Summary

Rank Expansion Networks (ReXNets) follow a set of new design 
principles for designing bottlenecks in image classification models.

## Usage

import timm
m = timm.create_model('rexnet_100', pretrained=True)
m.eval()
```

In this case, you just need to include this markdown file into the global `model-index.yml` file:

```yaml
Models:
  - docs/rexnet.md
```

## Get started

Check out our [official documentation](https://model-index.readthedocs.io/en/latest/) on how to get started. 

## Uploading to Papers with Code

To feature your library on Papers with Code, get in touch with `hello@paperswithcode.com` and the model index
of your library will be automatically included into Papers with Code. 







