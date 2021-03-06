.. CrypTen documentation master file, created by sphinx-quickstart on Thu Sep 12 20:49:44 2019.  You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

CrypTen Documentation
=====================
CrypTen is a Privacy Preserving Machine Learning framework written using `PyTorch
<http://pytorch.org/>`_ that allows researchers and developers to
train models using encrypted data. CrypTen currently supports
`Secure multi-party computation
<https://en.wikipedia.org/wiki/Secure_multi-party_computation>`_ as its encryption
mechanism.

.. toctree::
    :hidden:

    self
    aws

Installation on Linux and Mac
=============================

We recommend installing CrypTen in its own ``conda`` environment. Please install
``Anaconda Python 3.7`` before doing the following steps

For Linux

.. code-block:: bash

    $ conda create -n crypten-env python=3.7
    $ conda activate crypten-env
    $ conda install pytorch torchvision cpuonly -c pytorch-nightly

For Mac

.. code-block:: bash

    $ conda create -n crypten-env python=3.7
    $ conda activate crypten-env
    $ conda install pytorch torchvision -c pytorch-nightly

For both

.. code-block:: bash

    $ git clone git@github.com:facebookresearch/CrypTen.git
    $ cd CrypTen; pip install -e .


To check if your installation is working, you can run the unit tests as follows

.. code-block:: bash

    $ python3 -m unittest discover test

We do not support Windows yet.

Examples
========

To run the examples in the ``examples`` directory, you additionally need to do
the following

.. code-block:: bash

    $ pip install -r requirements.examples.txt

We have the following examples, covering a range of models

- The linear SVM example, ``mpc_linear_svm``, generates random data and trains a
  SVM classifier on encrypted data.
- The LeNet example, ``mpc_cifar``, trains an adaptation of LeNet on CIFAR in
  cleartext and encrypts the model and data for inference
- The TFE benchmark example, ``tfe_benchmarks``, trains three different network
  architectures on MNIST in cleartext, and encrypts the trained model and data
  for inference
- The bandits example, ``bandits``, trains a contextual bandits model on
  encrypted data (MNIST)
- The imagenet example, ``mpc_imagenet``, does inference on pretrained model from
  ``torchvision``

For examples that train in the cleartext, we also provide pre-trained models in
cleartext in ``model`` subdirectory of each example.

You can check all example specific command line options by doing the following;
shown here for ``tfe_benchmarks``

.. code-block:: bash

    $ python3 examples/tfe_benchmarks/launcher.py --help

Some MPC specific options are

- ``--world_size`` Number of peers in MPC
- ``--multiprocess`` Run in multiprocess mode on one machine, where each peer is a
  separate process

Examples on AWS
---------------

CrypTen also provides a script ``aws_launcher`` to launch examples with
encrypted data on multiple AWS instances. See :doc:`aws`.

.. toctree::
    :maxdepth: 3
    :caption: Package Reference

    crypten.CrypTensor <cryptensor>
    crypten.MPCTensor <mpctensor>
    crypten.AutogradCrypTensor <autogradcryptensor>
    crypten.nn <nn>

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
