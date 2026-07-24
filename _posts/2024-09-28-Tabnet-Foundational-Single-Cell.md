---
layout: post
title: "TabNet: a deep learning architecture for interpretable tabular data"
date: 2024-09-28
tags: [Deep Learning, Single-cell]
excerpt: "How TabNet's sequential attention works, and why sparse feature selection makes it an appealing backbone for single-cell RNA foundation models."
---

TabNet represented an advancement in the ability of deep learning to handle tabular data, offering both high performance and interpretability. This post explores its architecture and the components that make it particularly effective for single-cell RNA analysis.

## Core architecture overview

TabNet processes data through a series of sequential steps, each contributing to the final prediction. What makes it unique is its ability to select relevant features at each decision step, similar to how humans make sequential decisions by focusing on different aspects of a problem.

### The building blocks

#### Feature Transformer

At the heart of TabNet lies the Feature Transformer, which consists of four consecutive Gated Linear Unit (GLU) blocks. Each GLU block comprises:

1. A fully connected layer
2. Batch normalization
3. A GLU activation function that performs element-wise multiplication between a sigmoid function and input features

This structure allows the model to learn complex feature interactions while maintaining computational efficiency.

#### Attentive Transformer

The Attentive Transformer is what gives TabNet its interpretability. It works by:

1. Creating masks that determine feature importance
2. Using a fully connected layer followed by batch normalization
3. Applying a sparsemax activation function with prior scales

The prior scales are particularly interesting: they start as ones and evolve based on feature usage across previous steps. This mechanism is controlled by a gamma parameter:

- Gamma close to 1: encourages the use of different features at each step
- Larger gamma values: promote consistent feature usage across steps

### Sequential processing

The model processes data in steps, where each step involves:

1. The Attentive Transformer creating a mask
2. The Feature Transformer using this mask to generate predictions
3. Outputs from each step being aggregated for the final prediction

### Interpretability features

TabNet offers several ways to interpret its decisions:

- Instance-wise feature importance through mask analysis
- Aggregated feature importance across steps
- The ability to track which features contribute most to specific predictions

## Advanced capabilities

### Handling different data types

TabNet can effectively work with:

- Numerical features
- Categorical features (through embeddings)
- Mixed data types

### Pretraining capabilities

The architecture supports self-supervised pretraining by predicting randomly masked features, similar to BERT's approach in NLP. This can significantly improve performance when labeled data is scarce.

### Foundation model requirements for scRNA

In single-cell RNA (scRNA), the data is represented as count matrices: dataframes where rows correspond to individual cells, columns represent genes, and the values indicate the number of reads from a given cell that mapped to each gene. The number of reads assigned to a gene can vary due to multiple factors, including the sequencing technology used, the length of the gene, and the size of the cell, among others. Once these technical biases are accounted for, the relationships between gene counts are expected to reflect the activation of different gene programs, driven by the cell's transcriptional state.

Some researchers have drawn parallels between scRNA data and natural language processing, adopting the "bag-of-words" concept and applying it to genes, a model known as "bag-of-genes". This approach captures gene interdependencies in a loose, language-like manner. However, given the limitations of current experimental sequencing technologies, these models may be more prone to learning technical noise rather than biologically meaningful signals. In contrast, models like TabNet, which emphasize sparse feature selection, could offer clearer and more interpretable outputs by focusing on the most relevant features and filtering out noise.

To serve as a foundation model for scRNA, TabNet needs to support:

1. **Label transfer.** TabNet trained in a supervised manner has been used as the model for supervised classification of cell types in a couple of papers (SIMS, scTab).
2. **Batch integration.** Categorical features representing the batch or disease could be used for batch integration.
3. **Gene perturbation prediction.** Pretrain TabNet in an unsupervised manner, forcing it to learn how the transcription levels of genes relate to each other.
