# Install deep learning frameworks.

## Table of contents

* [PyTorch](#pytorch)
* [TensorFlow](#tensorflow)
* [Keras](#keras)


Before you want to install any deep learning framework, you should first install a 'default' Python environment by following [this module](./python.md). Let's say the environment you install is called `X`. 

Everything below is only tested under Python 3.

In addition, Yimeng doesn't think using two frameworks in the same Python file is a good idea.

## PyTorch

Easy.

1. Go to the [official website](http://pytorch.org/)
2. Make the following choices regarding OS, Python, CUDA, etc.
	* OS = `Linux`, Package Manager = `pip`
	* Python version shoud be the same as the Python version of environment `X`.
	* CUDA should be have a version that is as new as possible as long as it is allowed by the NVIDIA driver on GPU cluster. Implicitly, the latest cuDNN compatible with this CUDA version is also chosen. As of 02/04/2018, we should choose CUDA 9 (bundled with cuDNN 7) for the cluster. 
		* There is a catch with the current old NVIDIA driver on the cluster. Current driver won't allow RNN operations to function properly. Check [release notes of cuDNN v7](http://docs.nvidia.com/deeplearning/sdk/cudnn-release-notes/rel_704.html#rel_704). 
3. Now follow commands on the website like the following. Change `pip3` to `pip`.
	
	~~~
	pip3 install http://download.pytorch.org/whl/cu80/torch-0.3.0.post4-cp36-cp36m-linux_x86_64.whl 
	pip3 install torchvision
	~~~
	
	* The first line installs PyTorch itself. The second line installs some computer vision-related goodies. If you do the second line, then it's better to first install `scikit-image` first (see. **additional packages** of [this module](./python.md)) to ensure most packages come from conda-forge, which is stable and good.


## TensorFlow

More tricky. The following instruction applies to TensorFlow 1.5.0.

### installation

* Install CUDA 9 and cuDNN v7. Follow [old wiki](https://github.com/leelabcnbc/lab-wiki-before-20170525/wiki/how-to-use-CNBC-cluster) to get a hint. Notice that you don't need to set alias for CUDA 9 any more.
* Install some additional dependencies by executing the following command.
	
	~~~
	# see <https://conda.io/docs/spec.html#package-match-specifications>. Need double quote.
	conda install -c conda-forge --no-update-dependencies "protobuf>=3.4.0" "mock>=2.0.0"
	~~~
* Install TensorFlow by executing the following command. Make sure you are on python version 3.6. There should be only two changes to existing packages (`bleach` and `html5lib`, as TensorBoard need specific versions of them), as of 02/04/2018.

	~~~
	pip install /data2/leelab/software/tensorflow/gpu/py36/tensorflow-1.5.0-cp36-cp36m-linux_x86_64.whl
	~~~

Check `/data2/leelab/software/tensorflow/` for other versions.

### usage

always run the following two lines first to make sure CUDA and cuDNN libraries can be found or add them to your ~/.bashrc

~~~
. ~/DevOps/env_scripts/add_cuda_lib_v9.sh
. ~/DevOps/env_scripts/add_cudnn_v7.sh
~~~




### alternative way for installation (easier, but may be messy later).

You can also try <https://anaconda.org/anaconda/tensorflow-gpu>. Yimeng doesn't like it mostly because Yimeng thinks the official anaconda repo may not play well with conda-forge sometimes. In addition, this anaconda version is not optimized for the CPUs on the cluster, compared to the one above compiled by Yimeng.

### alternative way 2 for installation (your own adventure).

Check <https://github.com/yaroslavvb/tensorflow-community-wheels>.


## Keras

* install TensorFlow.
* Simply follow the [official website](https://keras.io/) should be fine. For example, just type `pip install keras`.
