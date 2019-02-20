softmax regression
#####################

图例
*****************

Predicted function
********************

.. math:: f(\mathbf{x},k;\mathbf{k}) = \frac{
    \exp^{\mathbf{x}\mathbf{\Theta}_k}
    }
    {\sum\limits_{k=1}^{\mathbf{k}}{\exp^{\mathbf{x}\mathbf{\Theta}_k}
    }}

.. note:: 应该存在更简洁的表达方式,待查阅

Loss function
******************

.. math:: L(\mathbf{y},\mathbf{\bar{y}}) = - \prod_{k=1}^{\mathbf{k}}{\mathbf{y}_k \log{\mathbf{\bar{y}}_k}}

Object function
******************

.. math::

    \begin{align*}
    O(\mathbf{X},\mathbf{Y};\mathbf{\Theta}) & =  \prod_{i=1}^{m} L(\mathbf{Y}_i,\mathbf{\bar{Y}}_i) \\
                                             & = -  \prod_{i=1}^{m} \prod_{k=1}^{\mathbf{k}} {\mathbf{Y}}_{i}^{k} \log{\mathbf{\bar{Y}}_{i}^{k}}
    \end{align*}

Optimizing
*****************

Gradient-based
==================

.. image:: /_static/figure/softmax-Gradient-based.png


.. note:: 其中存在 :math:`(\exp^{\Theta_k \mathbf{X}_i})^{'} \text{、} \ \ (\sum\limits_{k=1}^{m} \exp^{\Theta_k \mathbf{X}_i})^{'}` 是对 :math:`\Theta_k \mathbf{X}_i` 求导.

