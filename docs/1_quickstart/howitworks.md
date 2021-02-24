# How it works

There is a root file for the model index: `model-index.yml` that contains (or links to) all the 
metadata in a consistent format. An example with a single model:

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

The fields present in this file as **common fields** that are automatically recognized by Papers with Code
and enable comparison across different models. You can also add any number of **custom fields** that are
specific to your model or library. 

## Storing metadata in markdown files

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
