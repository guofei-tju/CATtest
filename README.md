# RetroCaptioner

## Title
RetroCaptioner: Beyond Attention in End-to-end Retrosynthesis Transformer via Dynamically Integrated Learnable Graph Representation

## Abstract
In this work, we present RetroCaptioner, a novel end-to-end framework for one-step retrosynthesis that combines the power of a graph encoder, which integrates learnable structural information, with the capability to sequentially translate drugs, thereby efficiently capturing chemically plausible information. 

In the application of drug synthesis route planning, RetroCaptioner identifies shortened and optimal pathways that accurately correspond to established reactions, offering valuable insights for reliable and high-quality organic synthesis in drug discovery.
![image](model.png)

## Setup
RetroCaptioner requires anaconda with Python 3.7 or later, cudatoolkit=10.2.

Sugguest to install RetroCaptioner in a virtual environment to prevent conflicting dependencies.
```
conda create -n RetroCaptioner python==3.7
conda activate RetroCaptioner
conda install --yes --file requirements.txt
CUDA-enabled device for GPU training (optional)
```

## Training the model

To train the model, you will use the `train.py` script. This script accepts several command-line arguments to customize the training process.

## Command-Line Arguments:
* `--known_class`: Indicates whether the class is known (True) or unknown (False).
* `--checkpoint_dir`: Specifies the directory where the model checkpoints will be saved.
* `--device`: Designates the training device, either cuda:0 for GPU or cpu for CPU.

## Training command:

Run the following command to start the training process:

``` bash
$ python train.py --known_class 'True' --checkpoint_dir './checkpoint' --device cuda:0
```
Replace the argument values as per your requirements. For instance, use `--device`  cpu if you're training on a CPU.

## Planning

Demo code for multi-step planning has been placed in `run_biosynthesis.py`.

This demo now will take only 20 seconds with single GPU (Nvidia RTX3090). One need to first download the checkpoints and unzip under `path to folder` to run the demo. The output will be visulized in viz_dir.

The key functions are shown in the following block, You may run your own molecule by changing the 'target_mol' in `main_biosynthesis()`.

``` bash
 $ provide the code here 
``` 

## Validating the model

After training, you can validate the model's accuracy using the `translate.py` script.
* `--known_class`: As in the training step, this indicates whether the class is known or unknown.
* `--checkpoint_dir`: The directory where your trained model checkpoints are stored.
* `--checkpoint`: The specific checkpoint file to use for validation. Replace `{training_step}` with the appropriate training step number.
* `--device`: The device to run the validation on, either GPU (cuda:0) or CPU (cpu).


## Train the model and perform the retrosynthesis step
To train the model, please run the train.py file. After the training is completed, you can run the translate.py for one-step retrosynthesis prediction
