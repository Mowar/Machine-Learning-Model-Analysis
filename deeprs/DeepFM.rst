DeepFM
#########




compare
**********

DeepFM vs FNN
====================

FNN
------

- the embedding parameters might be over affected by FM

- the efficiency is reduced by the overhead introduced by the pre-training stage

- FNN captures only high-order feature interactions

DeepFM
----------

- DeepFM needs no pre-training
- learns both high- and low-order feature interactions

DeepFM vs PNN
========================

PNN
-----

- the outer product is less reliable than the inner product, since the approximated computation of outer product loses much information that makes the result unstable.

- inner product is more reliable, it still suffers from high computational complexity, because the output of the product layer is connected to all neurons of the first hidden layer.

- ignore low-order feature interactions

DeepFM
----------

- the output of the product layer in DeepFM only connects to the final output layer (one neuron)

DeepFM vs WDL
==================

WDL
-----

-  expertise feature engineering on the input to the “wide” part

DeepFM
--------

- handle the input by learning directly from the input raw features

feature embedding
***********************

- DeepFM outperforms the models that learn high- and low-order feature interactions using separate feature embeddings
