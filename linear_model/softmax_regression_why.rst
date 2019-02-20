softmax regression why
##########################

为什么预测函数是这样?
**************************
假设满足广义线性模型构造方法的三个假设情况下成立. 其中假设一
满足的情况下 :math:`P(\mathbf{y}|x;\phi,k) \sim \text{category}(\phi_1,\phi_2,...,\phi_i,...,\phi_k)` .由此存在如下的推导:

.. math::

    P(\mathbf{y};\theta,k) & = {\phi_1}^{\mathbf{y}_1} {\phi_2}^{\mathbf{y}_2}...{\phi_i}^{\mathbf{y}_i}...{\phi_k}^{ 1 - \sum\limits_{i=1}^{k-1}\mathbf{y}} \\
                           & = \exp^{ \mathbf{y}_1 \log{\phi_1} + \mathbf{y}_2 \log{\phi_2}+...+\mathbf{y}_i \log{\phi_i}+...+(1 - \sum\limits_{i=1}^{k-1}\mathbf{y}) \log{\phi_k}} \\
                           & = \exp^{ \mathbf{y}_1 \log{ \frac{\phi_1}{\phi_k}} + \mathbf{y}_2 \log{ \frac{\phi_2}{\phi_k}} +...+\mathbf{y}_{k-1} \log{ \frac{\phi_{k-1}}{\phi_k}} + \log{\phi_k} } \\
                           & = \exp^{  \begin{bmatrix} \log{ \frac{\phi_1}{\phi_k}} \\
                                                     \log{ \frac{\phi_2}{\phi_k}} \\
                                                     ... \\
                                                     \log{\frac{\phi_{k-1}}{\phi_k}} \\
                                                     \log{\frac{\phi_k}{\phi_k}}
                                                      \end{bmatrix}^T \mathbf{y}  - -\log{\phi_k}}

由上式可得: :math:`\eta=\begin{bmatrix} \log{ \frac{\phi_1}{\phi_k}} \\ \log{ \frac{\phi_2}{\phi_k}} \\ ... \\ \log{\frac{\phi_{k-1}}{\phi_k}} \\ \log{\frac{\phi_k}{\phi_k}} \end{bmatrix}`. 进一步可以得出:

.. math::

    \eta_i & = \log{\frac{\phi_i}{\phi_k}} \\
    \phi_i & = \phi_k \exp^{\eta_i} \\
    1 & = \sum\limits_{i=1}^{k} \phi_i = \phi_k \sum\limits_{i=1}^{k} \exp^{\eta_i} \\
    \phi_k & = \frac{1}{\sum\limits_{i=1}^{k} \exp^{\eta_i}}

把 :math:`\phi_k = \frac{1}{\sum\limits_{i=1}^{k} \exp^{\eta_i}}` 代入 :math:`\phi_i  = \phi_k \exp^{\eta_i}` 中,可得如下结果:

.. math:: \phi_i  =  \frac{ \exp^{\eta_i} }{\sum\limits_{i=1}^{k} \exp^{\eta_i}}

从假设二可以推导出:

.. math:: f(x) & =\mathbf{E}[\mathbf{y}|x;\phi] \\
               & = \begin{bmatrix}
                    \phi_1 \\
                    \phi_2 \\
                    ... \\
                    \phi_k
                   \end{bmatrix}

其中假设三 :math:`\phi_i=\theta_{i}^{T} \mathbf{x}`. 联立假设一、二、三的结果,可得:

.. math:: f(x) & = \begin{bmatrix}
                     \frac{ \exp^{\theta_{1}^{T} \mathbf{x}} }{\sum\limits_{i=1}^{k} \exp^{\theta_{i}^{T} \mathbf{x}}} \\
                     \frac{ \exp^{\theta_{2}^{T} \mathbf{x}} }{\sum\limits_{i=1}^{k} \exp^{\theta_{i}^{T} \mathbf{x}}} \\
                    ... \\
                    \frac{ \exp^{\theta_{k}^{T} \mathbf{x}} }{\sum\limits_{i=1}^{k} \exp^{\theta_{i}^{T} \mathbf{x}}}
                   \end{bmatrix}

.. note:: :math:`1 \leq i \leq k`

