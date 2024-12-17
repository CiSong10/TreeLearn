# TreeLearn: A deep learning method for segmenting individual trees from ground-based LiDAR forest point clouds
![methods](https://github.com/user-attachments/assets/1fe75b49-1a1e-450e-9c90-f5ab5d70adfc)

Laser-scanned point clouds of forests make it possible to extract valuable information for forest management. To consider single trees, a forest point cloud needs to be segmented into individual tree point clouds. Existing segmentation methods are usually based on hand-crafted algorithms, such as identifying trunks and growing trees from them, and face difficulties in dense forests with overlapping tree crowns. In this study, we propose TreeLearn, a deep learning-based approach for tree instance segmentation of forest point clouds. TreeLearn is trained on already segmented point clouds in a data-driven manner, making it less reliant on predefined features and algorithms. Furthermore, TreeLearn is implemented as a fully automatic pipeline and does not rely on extensive hyperparameter tuning, which makes it easy to use. Additionally, we introduce a new manually segmented benchmark forest dataset containing 156 full trees. The data is generated by mobile laser scanning and contributes to create a larger and more diverse data basis for model development and fine-grained instance segmentation evaluation. We trained TreeLearn on forest point clouds of 6665 trees, labeled using the Lidar360 software. An evaluation on the benchmark dataset shows that TreeLearn performs as well as the algorithm used to generate its training data. Furthermore, the performance can be vastly improved by fine-tuning the model using manually annotated datasets. We evaluate TreeLearn on our benchmark dataset and the Wytham Woods dataset, outperforming the recent SegmentAnyTree, ForAINet and TLS2Trees methods. The TreeLearn code and all datasets that were created in the course of this work are made publicly available.


The paper can be found [here](https://www.sciencedirect.com/science/article/pii/S1574954124004308). The data associated with the paper can be found [here](https://data.goettingen-research-online.de/dataset.xhtml?persistentId=doi:10.25625/VPMPID) and [here](https://data.goettingen-research-online.de/dataset.xhtml?persistentId=doi:10.25625/QUTUWU).

## Updates!! 🚀
* 【2024/01/16】 Provide a new version of ``model_weights_diverse_training_data.pth`` that produces visually more appealing results.
* 【2024/06/19】 Faster algorithm for propagation of results to original point cloud (speeds up inference⚡).
* 【2024/12/17】 📊 Updated evaluation script so that the evaluation protocol from the paper can be run with arbitrary methods and forest point clouds.
* 【2024/12/17】 🆕 Added new model weights that were trained on crops without statistical outlier filtering (speeds up inference⚡).

## Demo [Currently non-functional]
For a quick demo of the capabilities of TreeLearn without any manual setup, we prepared a google colab notebook: 

<a target="_blank" href="https://colab.research.google.com/github/ecker-lab/TreeLearn/blob/main/TreeLearn_Pipeline.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>  
</a> 

Due to an incompatibility between cuda 12.2 and spconv the colab notebook is currently **non-functional**. 

## Installation

To set up the environment we recommend Conda. If Conda is set up and activated, run the following: 

```
source setup/setup.sh
```

Depending on the specific gpu and cuda version of your system, you might need to adjust the spconv version specified in ``setup/requirements.txt``.

## Segmentation pipeline

If you are not interested in training your own models, but only want to use pre-trained weights for forest segmentation, we refer to the [segmentation pipeline guide](docs/segmentation_pipeline.md).

## Training

If you want to train a custom model for forest segmentation, we refer to the [training guide](docs/training.md)

## Evaluation

To evaluate the segmentation results of arbitrary methods on arbitrary benchmark datasets, we refer to the [evaluation guide](docs/evaluation.md)

## Acknowledgements

The code is built based on [SoftGroup](https://github.com/thangvubk/SoftGroup) and [spconv](https://github.com/traveller59/spconv).
