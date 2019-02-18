logistic regression
####################

图例
************

Predicted function
*******************

.. math:: f(x) = g(\mathbf{\theta}^T \mathbf{x}) = \frac{1}{ 1 + \exp{- \mathbf{\theta}^T \mathbf{x}}}

Loss function
******************

.. math::

    L(y,\bar{y}) = - (y \log {f(x)} + (1-y) \log {(1 - f(x))})

.. Note:: 还可以化简,待完善log(2+exp)形式

.. Note:: 该损失函数有一个专业名词

Objection function
*******************

.. math:: O(\mathbf{y},\mathbf{X}) =  \sum_{i=1}^{m} L(\mathbf{y}_i, f(\mathbf{X}_i)=- \sum_{i=1}^{m} {\mathbf{y}_i \log {f(\mathbf{X}_i)} + (1-\mathbf{y}_i) \log {(1 - f(\mathbf{X}_i))}}

Optimizing
**************

.. math:: \mathbf{\theta} = \mathop{\mathbf{\arg\min}}_{\mathbf{\theta}} \ \ O(\mathbf{y},\mathbf{X})

Gradient-based
=================

.. math::

    \nabla_{\theta} {O(\mathbf{y},\mathbf{X};\mathbf{\theta})} & = \nabla_{\theta} \ \  \sum_{i=1}^{m} L(\mathbf{y}_i,f(\mathbf{X}_i)) \\
                                                               & = \nabla_{\theta} \ \ - \sum_{i=1}^{m} {\mathbf{y}_i \log {f(\mathbf{X}_i) + (1 - \mathbf{y}_i) \log {(1 - f(\mathbf{X}_i ))}}} \\
                                                               & = \nabla_{\theta} \ \  - ({\mathbf{y}_i \log {f(\mathbf{X}_i) + (1 - \mathbf{y}_i) \log {(1 - f(\mathbf{X}_i ))}}} \\
                                                               & = - \frac{\partial{ \mathbf{y}_i \log {f(\mathbf{X}_i) + (1 - \mathbf{y}_i) \log {(1 - f(\mathbf{X}_i ))}} }}{ \mathrm{d}(\mathbf{\theta}^T \mathbf{X}_i)} \frac{\partial{\mathbf{\theta}^T \mathbf{X}_i}}{\mathrm{d}x} \\
                                                               & = - (\mathbf{y}_i \frac{1}{f(\mathbf{X}_i)}  + (1-y) \frac{1}{1 - f(\mathbf{X}_i)}) g(\mathbf{\theta}^T \mathbf{X}_i) ( 1 - g(\mathbf{\theta}^T \mathbf{X}_i)) \mathbf{X}_i \\
                                                               & = - (\mathbf{y}_i - f(\mathbf{X}_i)) \mathbf{X}_i

根据上式子,可以得出参数更新规则:

.. math:: \mathbf{\theta} \leftarrow \mathbf{\theta} - \alpha (- (\mathbf{y}_i - f(\mathbf{X}_i)) \mathbf{X}_{i} )

