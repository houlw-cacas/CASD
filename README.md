# Comprehensive Attention Self-Distillation(CASD) -(In progress)

This is the official implementation of the paper: 
- Zeyi Huang*, Yang Zou*, Vijayakumar Bhagavatula, Dong Huang, Comprehensive Attention Self-Distillationfor Weakly-Supervised Object Detection, Neural Information Processing Systems(NeurIPS), 2020. (* indicates equal contribution) [PDF in Arxiv](https://arxiv.org/abs/2010.12023)


## Requirements:

- Python >=3.6
- Pytorch >=1.1.0
- Torchvision >= 0.3.0
- Cuda >=10.0
- cython
- matplotlib
- opencv
- scipy
- sklearn
- GPU: TITAN RTX(24G of memory)

## Installation

1. Clone the repository
```bash
  git clone
```
2. Compile the CUDA code
```bash
  cd CASD/lib
  bash make_cuda.sh
```

## Data Preparation

1. Download the training, validation, test data and the VOCdevkit
```bash
  mkdir data
  cd data/
  wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtrainval_06-Nov-2007.tar
  wget http://host.robots.ox.ac.uk/pascal/VOC/voc2007/VOCtest_06-Nov-2007.tar
  wget http://host.robots.ox.ac.uk/pascal/VOC/voc2012/VOCdevkit_18-May-2011.tar
```

2. Extract all of these tars into one directory named VOCdevkit
```bash
  tar xvf VOCtrainval_06-Nov-2007.tar
  tar xvf VOCtest_06-Nov-2007.tar
  tar xvf VOCdevkit_08-Jun-2007.tar
```

3. Create symlinks for PASCAL VOC dataset
```bash
  cd CASD/data
  ln -s VOCdevkit VOCdevkit2007
```

4. Download pretrained ImageNet weights from here, and put it in the data/imagenet_weights/.

5. Download selective search proposals from here, and put it in the data/selective_search_data/.

## Training and Testing
Train a vgg16 Network on VOC 2007 trainval
```bash
  bash experiments/scripts/train_faster_rcnn.sh 0 pascal_voc vgg16
```

Test a vgg16 Network on VOC 2007 test
```bash
  bash experiments/scripts/test_faster_rcnn.sh 0 pascal_voc vgg16
```

## Acknowledgement
We borrowed code from [MLEM](https://github.com/vasgaowei/pytorch_MELM), [PCL](https://github.com/ppengtang/pcl.pytorch), and [Faster-RCNN](https://github.com/jwyang/faster-rcnn.pytorch).

### Citation: 

```bash
@inproceedings{huangCASD2020,
  title={Comprehensive Attention Self-Distillationfor Weakly-Supervised Object Detection},
  author={Zeyi Huang and Yang Zou and Vijayakumar Bhagavatula and Dong Huang},
  booktitle={NeurIPS},
  year={2020}
}
```
