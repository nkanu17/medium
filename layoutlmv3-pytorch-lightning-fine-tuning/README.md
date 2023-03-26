# Fine-tune LayoutLMv3 for Token Classification with PyTorch Lightning

## [Click here to read on Medium](https://medium.com/@nitinkanukolanu/fine-tuning-layoutlmv3-for-token-classification-with-pytorch-lightning-87c21aacc9e3)

## Overview
The objective in this notebook is to show how to fine-tune LayoutLMv3 for token classification using *PyTorch Lightning*.


The LayoutLM family of models, [developed by Microsoft](https://github.com/microsoft/unilm), have gained a lot of popularity in the field of document understanding. The models are able to handle a wide range of documents, including structured, semi-structured, and unstructured documents, and identify different elements such as texts, tables, and images to extract relevant information. This versatility makes them suitable for various document understanding tasks , such as form recognition, key information extraction, document layout analysis, and many more.

In this article, we will demonstrate how to fine-tune LayoutLMv3 for token classification using [PyTorch Lightning](https://lightning.ai/docs/pytorch/stable/), a machine learning framework built on top of native PyTorch. Although other implementations of fine-tuning LayoutLMv3 already exist, this article aims to also discuss some of the advantages of using PyTorch Lightning.


[LayoutLMv3](https://arxiv.org/abs/2204.08387), a state of the art model in the field Document AI, involves understanding the structure and organization of documents, such as identifying text blocks, tables, figures, and other visual and textual elements. It is a new and improved version based on it's predecessors LayoutLM and LayoutLMv2.

The LayoutLMv3 model is capable of processing both the visual content (images) and textual content of documents simultaneously, which makes it highly effective for tasks like document classification (sequence classification), information extraction (token classification), and question answering.

Other approaches to fine-tune this model can be found through [Niels Rogge's LayoutLMv3 Tutorials](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/LayoutLMv3/Fine_tune_LayoutLMv3_on_FUNSD_(HuggingFace_Trainer).ipynb).

**Acknowledgement**
- A big thanks to [Niels Rogge](https://github.com/NielsRogge) and their awesome [Transformers Tutorials](https://github.com/NielsRogge/Transformers-Tutorials.ipynb). I have learned a lot from their posts about using differnet SOTA models with Huggingface transformers.

**Advantages of PyTorch Lightning**

PyTorch Lightning is an open-source machine learning framework built by [Lightning AI](https://github.com/Lightning-AI)). It provides a high-level interface for machine learning experimentation, making it quicker and easier to train and test models. It is built around PyTorch, whose main difference is that it creates a new modular and object oriented approach to writing machine learning code. Some of the key advantages of PyTorch Lightning include:
- High-level interface
    - PyTorch Lightning automates many repetitive tasks associated with training deep learning models, we will see this in action below.
- Standardized structure and modularity
    - The framework promotes a clear separation between different parts of the model, such as the training loop, validation loop, and model architecture. It introduced the LightningDataModule and LightningModule, which allow improved readability, reusability, and easier integration with experimenting with different datasets and models.
- Automated Distributed training
    - One of the challenging and tedious aspects of training deep learning models is writing distributed training code. PyTorch Lightning takes away this complexity by providing built-in support for various distributed training strategies through a simple configuration within it's trainer.
- Integration with external experiment tools
    - Another key aspect of any machine learning project is experiment tracking.  PyTorch Lightning offers automatic integration with popular tools such as TensorBoard, MLflow, CometML, and Weights & Biases.
- Large community support
    - Community support for any project is important as it keeps them up-to-date. Imagine using a powerful frameowork that experiences a sudden stoppage in development (like Detectron2 :) ) - that would'nt be nice would it? - PyTorch Lightning is backed by an active open-source community and the LightningAI team, ensuring continuous development and improvement.
- Many more, I would encourage you to checkout their [repo](https://github.com/Lightning-AI/lightning) or [docs](https://lightning.ai/docs/pytorch/stable/)!

# Table of Contents
- Step 1: Setup environment
- Step 2: Obtain and observe the dataset and encodings
- Step 3: Prepare data with the LightningDataModule
- Step 4: Build the Lightning Module for Modeling
- Step 5: Define the Trainer and train the model
