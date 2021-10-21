# mlj21DALC






------------------------------------------------------------------------------------------
	                   Readme for the DALC package
	 		       version Oct, 2021
------------------------------------------------------------------------------------------

The package includes the code of DALC, which solves the deep noisy label learning problem by a dual active query strategy using 
labels of two sources of instances[1].

[1] S.-Y. Li, Y. Shi, S.-J. Huang and S. Chen. Improving Deep Label Noise Learning with Dual
Active Label Correction. Machine Learning, 2021, in press.
 

ATTN: 
- This package is free for academic usage. You can run it at your own risk. For other
  purposes, please contact Ms. Shao-Yuan Li(lisy@nuaa.edu.cn).

- This package was developed by Ms. Shao-Yuan Li (lisy@nuaa.edu.cn). For any
  problem concerning the code, please feel free to contact Ms. Li.

------------------------------------------------------------------------------------------


# Improving Deep Label Noise Learning with Dual Active Label Correction

This is a PyTorch implementation of the Improving Deep Label Noise Learning with Dual Active Label Correction (Machine Learning)

```

```

## Requirements:

- TensorFlow == 1.15.0
- PyTorch >= 1.8.1

## Run:

Important options:

```shell
Forward:
--data_path: root path of dataset
--dataset: which dataset to run
--cprob: synthetic noise ratio
--ctype: synthetic noise type
DALC:
--data_path: root path of dataset
--dataset: which dataset to run
--cprob: synthetic noise ratio
--ctype: synthetic noise type
--atype: selecting strategy
--select_ratio, -sr: the instances ratio of each iteration
--iterations, -it: the number of iterations 
```

Before running, please download corresponding dataset and set the data path `--data_path`.

Run on CIFAR-10:

```shell
# firstly run forward to initialize
python forward-cifar.py --dataset cifar10 -cprob 0.4 -ctype flip
# then we run dalc
python dalc-cifar.py --dataset cifar10 -cprob 0.4 -ctype flip -sr 0.05 -it 6 -atype dalc-e
```

Run on CIFAR-100:

```shell
# firstly run forward to initialize
python forward-cifar.py --dataset cifar100 -cprob 0.4 -ctype flip
# then we run dalc
python dalc-cifar.py --dataset cifar100 -cprob 0.4 -ctype flip -sr 0.05 -it 6 -atype dalc-e
```

Run on MNIST:

```shell
--peu_times: ratio of pseudo labels to the selected instances
```

```shell
# firstly run forward to initialize
python forward-mnist.py -ctype flip
# then we run dalc
python dalc-cifar.py -ctype flip -sr 0.0003 -peu_times 50 -atype entropy+Least_entropy
```

Run on Clothing1M:

```shell
# firstly run forward to initialize
python forward-mnist.py
# then we run dalc
python dalc-cifar.py -sr 0.05 -it 1 -atype dalc-e
```

