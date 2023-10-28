# Energy efficient predictive coding networks

### Description
Supplementary material for 'Predictive coding is a consequence of energy efficiency in recurrent  neural networks'

### Dependencies

```pip install -r requirements.txt```

Or look in requirements.txt - be sure to use Python >=3.7

### Usage Notes:
- To replicate the results in the paper, please run results.sh (which in turn calls all of the figure generators) - takes 1h15m on a Mac M1
- trained models can be found [here](https://osf.io/c57d4/), but if you want to train your own models you can run train_models.py to produce the model instances used in determining the model preactivations:
- Also see [paper_results.ipynb](https://github.com/KietzmannLab/EmergentPredictiveCoding/blob/master/paper_results.ipynb) - but not that this is no longer current

```python train_models.py```


The script will automatically run on a gpu if a gpu is available and cuda is set up. Otherwise the script will revert back to cpu. If multiple gpu nodes are available, you can select which node you want the script to run on by prepending CUDA_VISIBLE_DEVICES, i.e:

```CUDA_VISIBLE_DEVICES=GPU_ID python train_models.py```

### Data Sets
We use the MNIST database of handwritten digits and CIFAR10, a labelled subset of the tiny image database . We created wrappers (mnist.py, cifar.py) that loads and transforms the images into sequences in ascending class order (with wraparound from class 9 to class 0). The sequenced data set is used as data for the networks. The appropriate training and test data can be created by simply calling: 

```import mnist```

```training_set, validation_set, test_set = mnist.load(val_ratio=0.0)```
for MNIST and:

```import cifar```

```training_set, validation_set, test_set = mnist.load(val_ratio=0.0, color=True)```
for CIFAR10. 
The (batches of) sequences can then be generated by:


``` batches, labels = dataset.create_batches(batch_size=batch_size, sequence_length=sequence_length, shuffle=True)```


Where 'dataset denotes training_set, validation_set or test_set'. 

### Usage Conditions
If you use this code in your work, we ask you to please cite:
Ali, A., Ahmad N., de Groot E., van Gerven M.A.J., Kietzmann T.C. (2021). **Predictive coding is a consequence of energy efficiency in recurrent neural networks.** doi: https://doi.org/10.1101/2021.02.16.430904

### TODO

- Fix runtime warnings on fig*.py
- Add metal support to speed up things on a M1 Mac


### M1 acceleration

The operator 'aten::sgn.out' was recently (as of 10.26.2023) added to PyTorch, so you'll need a nightly
build to install support for it


```pip3 install --pre torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/nightly/cpu```
