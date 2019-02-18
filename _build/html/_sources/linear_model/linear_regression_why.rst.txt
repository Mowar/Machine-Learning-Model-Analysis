linear regression why
######################

预测函数为什么是这样的?
***********************
答: 假设满足广义线性模型构造方法的三个假设情况下成立. 其中假设一满足的情况下 :math:`P(y|x;\theta) \sim \mathcal{N}(\mu, \sigma^2)` .由此存在如下的推导:

.. math::

    P(y;\mu) =& \frac{1}{\sqrt{2\pi}} \exp(-\frac{1}{2}(y-\mu)^2) \\
             =& \frac{1} {\sqrt{2\pi} } \exp(-\frac{1}{2}y^2).\exp(\mu y - \frac{1}{2}\mu^2)

由此可得: :math:`\eta = \mu`.在假设二成立的情况下,可以得出:

.. math:: f(x) & =\mathbf{E}[y|x;\theta] \\
               & = \mu
               
其中假设三 :math:`\eta=\theta^T \mathbf{x}` . 联立假设一、二、三,可得:

.. math:: f(x) = \theta^T \mathbf{x}

损失函数为什么是二次函数?
*************************

答:假设误差项 :math:`\epsilon \sim \mathcal{N}(0,\sigma^2)`. 由于:

.. math:: y = \mathbf{\theta}^T \mathbf{x} + \epsilon

所以:

.. math:: P(y:x;\mathbf{\theta}) = \frac{1}{\sqrt{2 \pi}} \exp ({- \frac{(y-\mathbf{\theta}^T \mathbf{x} )^2 }{2 \sigma^2}})

最大似然估计可得:

.. math::

    L(\mathbf{\theta})= & \prod_{i=1}^{m} P( \mathbf{y}_{i}| \mathbf{X}_{i} ; \mathbf{\theta}) \\
     \ell = & \log { \prod_{i=1}^{m}P(\mathbf{y}_{i}|\mathbf{X}_{i};\mathbf{\theta}) } \\
     = & \log { \prod_{i=1}^{m} \frac{1}{\sqrt{2\pi}\sigma} \exp{(- \frac{ (\mathbf{y}_{i} - \mathbf{\theta}^T\mathbf{X}_{i})^2}{2 \sigma^2})} } \\
     = & \sum_{i=1}^{m} \log { - \frac{1}{\sqrt{2\pi} \sigma} \exp(- \frac{(\mathbf{y}_i - \mathbf{\theta}^T \mathbf{X}_i)^2}{2 \sigma^2}) } \\
     = & m \log{\frac{1}{\sqrt{2 \pi} \sigma } } - \frac{1}{\sigma^2} . \frac{1}{2} \sum_{i=1}^{m} (\mathbf{y}_i - \mathbf{\theta} \mathbf{X}_i)^2 \\
     \approxeq & - \frac{1}{2} \sum_{i=1}^{m} (\mathbf{y}_i - \mathbf{\theta} \mathbf{X}_i)^2

所以最大似然等价于最小平方损失函数.

