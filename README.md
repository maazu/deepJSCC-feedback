# DeepJSCC-f: Deep Joint Source-Channel Coding of Images with Feedback

Code used in paper [DeepJSCC-f: Deep Joint Source-Channel Coding of Images with Feedback](https://arxiv.org/abs/1911.11174), appearing in IEEE Journal on Selected Areas in Information Theory (JSAIT).


- [Arxiv](https://arxiv.org/abs/1911.11174)
- [IEEE JSAIT](https://ieeexplore.ieee.org/document/9066966)


Authors: David Burth Kurka and Deniz Gündüz

**Google Collab Documentation For deepJSCC-feedback**
---

This guide will help you to setup kurka's into google collab. 

[Open your google](https://colab.research.google.com/notebooks/)

To setup the development evrioment we will begin by checking our current working directory. <br> 
```
import os
print(os.getcwd())
!ls
```
By defaut google collab run in /content in order save our progress, we will store the data in our google drive. <br>
Run this code to mount your google drive
<br>
```
from google.colab import drive
drive.mount('/content/drive')
```
Once the drive is mounted you will drive folder in the files sections 
change your current working directory by running this code cell

```
%cd /content/drive/My Drive/Colab Notebooks/
```
**YOU SHOULD RUN THIS STEP ONLY IF YOU DON'T have KURKA'S DATA in your directory otherwise skip this step **<br>
To fetch the repo data directly from kurka's git
```
! git clone https://github.com/kurka/deepJSCC-feedback.git 
```

Next we will assign ourself a GPU.<br>
Click the Edit Menu then click to Notebook Settings in change the Hardware setting to GPU -> click save. 
<br>
Congratualtion ! You have done alot ! but we still need to few more things.
<br>

Now we need to install the compatiable libaraires by running the following code into the cell.
```
!pip install ConfigArgParse
!pip install tensorflow==1.15
!pip install tensorflow-compression
```

Once the installation is completed, Make sure you are in the following directory
```
!ls 
#change directory to 
%cd /content/drive/My Drive/Colab Notebooks/deepJSCC-feedback/
```
Once the tensorlow is installed to check the gpu must be allocated to you the output should produce 1.
```
import tensorflow as tf
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))
```
---
**KURKA Code running examples**
---

Now if you have followed all the steps correctly, then you should be run the following following command.
```
!python jscc.py --help
```

OUTPUT SHOULD LOOK LIKE THIS 
```
usage: jscc.py [-h] [-c MY_CONFIG] --conv_depth CONV_DEPTH --n_layers N_LAYERS
               [--channel {awgn,fading,fading-real}] [--model_dir MODEL_DIR]
               [--eval_dir EVAL_DIR] [--delete_previous_model]
               [--channel_snr_train CHANNEL_SNR_TRAIN]
               [--channel_snr_eval CHANNEL_SNR_EVAL] [--feedback_noise]
               [--feedback_snr_train FEEDBACK_SNR_TRAIN]
               [--feedback_snr_eval FEEDBACK_SNR_EVAL]
               [--learn_rate LEARN_RATE] [--run_eval_once]
               [--train_epochs TRAIN_EPOCHS]
               [--batch_size_train BATCH_SIZE_TRAIN]
               [--batch_size_eval BATCH_SIZE_EVAL]
               [--epochs_between_evals EPOCHS_BETWEEN_EVALS]
               [--dataset_train {cifar,imagenet,kodak}]
               [--dataset_eval {cifar,imagenet,kodak}]
               [--data_dir_train DATA_DIR_TRAIN]
               [--data_dir_eval DATA_DIR_EVAL]
               [--pretrained_base_layer PRETRAINED_BASE_LAYER]
               [--target_analysis]
```

If the help is working without any error you then you can run this simple command code to fire your modal. So far it's not working well, but this will help you to get started. 

```
!python jscc.py --dataset_train kodak --conv_depth 3 --n_layers 3
```
**OUTPUT SHOULD LOOK LIKE THIS** 
```
#######################################
Current execution paramenters:
batch_size_eval: 128
batch_size_train: 128
channel: awgn
channel_snr_eval: 1
channel_snr_train: 1
conv_depth: 3.0
data_dir_eval: /tmp/train_data
data_dir_train: /tmp/train_data
dataset_eval: cifar
dataset_train: kodak
delete_previous_model: False
epochs_between_evals: 30
eval_dir: /tmp/train_logs/eval
feedback_noise: False
feedback_snr_eval: 20
feedback_snr_train: 20
learn_rate: 0.0001
model_dir: /tmp/train_logs
my_config: None
n_layers: 3
pretrained_base_layer: None
run_eval_once: False
target_analysis: False
train_epochs: 10000
...................................
...................................
...................................
```
