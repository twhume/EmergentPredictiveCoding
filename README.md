# Energy efficient predictive coding networks

### Description
Supplementary material for 'Predictive coding is a consequence of energy efficiency in recurrent  neural networks'

### Dependencies
1. Numpy
2. Matplotlib
2. PyTorch 1.4.0
3. Python  >= 3.7 

### Usage Notes:
- To replicate the results in the paper, please see [paper_results.ipynb](https://github.com/KietzmannLab/EmergentPredictiveCoding/blob/master/paper_results.ipynb)  
- The repository already contains trained models, but if you want to train your own models you can run train_models.py to produce the 10 model instances used in determining the model preactivations:

```python train_models.py```


The script will automatically run on a gpu if a gpu is available and cuda is set up. Otherwise the script will revert back to cpu. If multiple gpu nodes are available, you can select which node you want the script to run on by prepending CUDA_VISIBLE_DEVICES, i.e:

```CUDA_VISIBLE_DEVICES=GPU_ID python train_models.py```

### Data Set
We use the MNIST database of handwritten digits. We created a wrapper 'mnist.py' that loads and transforms the mnist digits into sequences of digits in ascending order (with wraparound from 9 to 0). The sequenced data set is used as data for the networks. The appropriate training and test data can be created by simply calling: 

```import mnist```

```training_set, validation_set, test_set = mnist.load(val_ratio=0.0)```


The (batches of) sequences can then be generated by:


``` batches, labels = dataset.create_batches(batch_size=batch_size, sequence_length=sequence_length, shuffle=True)```


Where 'dataset denotes training_set, validation_set or test_set'. 


### Usage Conditions
If you use this code in your work, we ask you to please cite:
Ali, A., Ahmad N., de Groot E., van Gerven M.A.J., Kietzmann T.C. (2021). **Predictive coding is a consequence of energy efficiency in recurrent neural networks.** doi: https://doi.org/10.1101/2021.02.16.430904










