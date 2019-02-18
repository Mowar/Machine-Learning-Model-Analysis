linear regression
###################

图例
***********

Predicted function
*******************

.. math::

    f(\mathbf{x}) =
    \begin{bmatrix}
    \theta_0 \\
    \theta_1 \\
    .. \\
    \theta_n
    \end{bmatrix}^T
    \begin{bmatrix}
    \mathbf{x}_0 \\
    \mathbf{x}_1 \\
    .. \\
    \mathbf{x}_n
    \end{bmatrix}
    =\mathbf{\theta}^T \mathbf{x}

Loss function
**************

.. math:: L(y,\bar{y}) = (y - \bar{y})^2


Object function
****************

.. math:: O(\mathbf{y},\mathbf{X}) = \frac{1}{2} \sum_{i=1}^{m}L(\mathbf{y}_{i},f(\mathbf{X}_i))=(\mathbf{y} - \mathbf{X}\mathbf{\theta})^T(\mathbf{y} - \mathbf{X}\mathbf{\theta})


Optimizing
************

.. math::

    \mathbf{\theta} = \mathop{\mathbf{\arg\min}}_{\mathbf{\theta}} \ \ \frac{1}{2} O(\mathbf{y},\mathbf{X})

Normal equations
=================

.. math::

    \nabla_{\theta} {O(\mathbf{y},\mathbf{X};\mathbf{\theta})} & =  \nabla_{\theta}  \ \ \frac{1}{2}(\mathbf{y} - \mathbf{X}\mathbf{\theta})^T (\mathbf{y} - \mathbf{X}\mathbf{\theta}) \\
                                                               & = \frac{1}{2} \nabla_{\theta} \ \ (\mathbf{\theta}^T \mathbf{X}^T \mathbf{X} \mathbf{\theta} - \mathbf{\theta}^T \mathbf{X}\mathbf{y} - \mathbf{y}^T\mathbf{X}\mathbf{\theta} + \mathbf{y}^T\mathbf{y}) \\
                                                               & = \frac{1}{2} \nabla_{\theta} \ \ \text{Tr}(\mathbf{\theta}^T \mathbf{X}^T \mathbf{X} \mathbf{\theta} - \mathbf{\theta}^T \mathbf{X}\mathbf{y} - \mathbf{y}^T\mathbf{X}\mathbf{\theta} + \mathbf{y}^T\mathbf{y}) \\
                                                               & = \frac{1}{2} \nabla_{\theta} \ \ (\text{Tr}(\mathbf{\theta}^T \mathbf{X}^T \mathbf{X}\mathbf{\theta}) - 2 \text{Tr}(\mathbf{y}^T\mathbf{X}\mathbf{\theta})) \\
                                                               & = \frac{1}{2} (\mathbf{X}^T \mathbf{X} \mathbf{\theta} + \mathbf{X}^T \mathbf{X}\mathbf{\theta} - 2 \mathbf{X}^T \mathbf{y}) \\
                                                               & = \mathbf{X}^T \mathbf{X} \mathbf{\theta} - \mathbf{X}^T \mathbf{y}

令 :math:`\nabla_{\theta}{O(\mathbf{y},\mathbf{X};\mathbf{\theta})} = 0`,得

.. math::

    \mathbf{X}^T \mathbf{X} \mathbf{\theta} & = \mathbf{X}^T \mathbf{y} \\
                                            \mathbf{\theta} & = \begin{cases}
                                                                    (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} & \text{Tr}{\mathbf{X}} = \text{Tr}{\mathbf{X}^T}\\
                                                                    (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} & \text{pass}
                                                                \end{cases}

.. Warning:: 若特征矩阵不是方阵,的情况。。。。待查询相关资料

.. Note:: 求解过程需要相关矩阵迹的知识

Gradient-based
===================

.. math::

    \nabla_{\theta} {O(\mathbf{y},\mathbf{X};\mathbf{\theta})} & = \nabla_{\theta} \ \ \frac{1}{2} \sum_{i=1}^{m} L(\mathbf{y}_i,f(\mathbf{X}_i)) \\
                                                               & = \nabla_{\theta} \ \ \frac{1}{2} \sum_{i=1}^{m} (\mathbf{y}_i - \mathbf{\theta}^T \mathbf{X}_i)^2 \\
                                                               & = \nabla_{\theta} \ \ \frac{1}{2} (\mathbf{y}_i - \mathbf{\theta}^T \mathbf{X}_i )^2 \\
                                                               & = \frac{1}{2} * 2 (\mathbf{y}_i - \mathbf{\theta}^T \mathbf{X}_i) \frac{\partial{(-\mathbf{\theta}^T \mathbf{X}})}{\mathrm{d}{\theta}} \\
                                                               & = - (\mathbf{y}_i - \mathbf{\theta}^T \mathbf{X}_i) \mathbf{X}_{i}

根据上式子,可以得出参数更新规则:

.. math:: \mathbf{\theta} \leftarrow \mathbf{\theta} - \alpha (- (\mathbf{y}_i - f(\mathbf{X}_i)) \mathbf{X}_{i} )

