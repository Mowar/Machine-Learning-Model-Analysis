logistic regression why
#########################

预测函数为什么是这样的?
***********************

假设满足广义线性模型构造方法的三个假设情况下成立. 其中假设一
满足的情况下 :math:`P(y|x;\theta) \sim \text{Bernoulli}(\phi)` .由此存在如下的推导:

.. math::

    P(y;\phi) = & \phi^y(1-\phi)^{1-y} \\
              = & \exp{ (y\log{\phi} + (1-y)\log{(1 - \phi)} ) } \\
              = & \exp{ (( \log{ (\frac{\phi}{1 - \phi} } ))y + \log{(1-\phi)} )}

由上式可得: :math:`\eta=\log{\frac{\phi}{1 - \phi}}`. 在假设二成立的情况下,可以得出:

.. math:: f(x) & =\mathbf{E}[y|x;\theta] \\
               & = \phi

其中假设三 :math:`\phi=\theta^T \mathbf{x}`. 联立假设一、二、三,可得:

.. math:: f(x) = \frac{1}{1 + \exp{- \mathbf{\theta}^T \mathbf{x}}}

损失函数为什么是交叉熵?
*************************

由对数几率(odd):

.. math:: \log{\frac{y}{1-y}} = \mathbf{\theta}^T \mathbf{x}

可以得出:

.. math::

    P(y=1|x;\mathbf{\theta}) & = f(\mathbf{x}) \\
    P(y=0|x;\mathbf{\theta}) & = 1 - f(\mathbf{x})

化简可得:

.. math:: P(y|x;\mathbf{\theta}) = f(\mathbf{x})^y (1 - f(\mathbf{x}))^{1-y}

最大似然估计可以得出:

.. math::

    L(\mathbf{\theta}) & = \prod_{i=1}^{m}P(\mathbf{y}_i|\mathbf{X}_i;\mathbf{\theta}) \\
    \ell               & = \log{\prod_{i=1}^{m}P(\mathbf{y}_i|\mathbf{X}_i;\mathbf{\theta})} \\
                       & = \log{ \prod_{i=1}^{m} f(\mathbf{X}_i)^{\mathbf{y}_i} (1 - f(\mathbf{X}_i))^{1-\mathbf{y}_i} } \\
                       & = \sum_{i=1}^{m} {\mathbf{y}_i \log{f(\mathbf{X}_i)} + {(1-\mathbf{y}_i)} \log{(1 - f(\mathbf{X}_i))}}

所以最大似然估计等价于最小化交叉熵损失函数.
