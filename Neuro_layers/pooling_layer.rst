pooling layer
###############

图例
************

表达式
*************

最大池化
=============

一维
----------

.. math:: O(m) = \sum\limits_{i=m}^{w+m} I(i) K(i)

.. math:: K(i) = \begin{cases}
                            1 & if \ \ I(i) \text{is maximum} \\
                            0 & else \ \ \text{other}
                    \end{cases}

二维
----------

.. math:: O(m,n) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n} I(i,j) K(i,j)

.. math:: K(i,j) = \begin{cases}
                            1 & if \ \ I(i,j) \text{is maximum} \\
                            0 & else \ \ \text{other}
                    \end{cases}

三维
---------

.. math:: O(m,n) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n} \sum\limits_{k=z}^{l+z} I(i,j,k) K(i,j,k)

.. math:: K(i,j,k) = \begin{cases}
                            1 & if \ \ I(i,j,k) \text{is maximum} \\
                            0 & else \ \ \text{other}
                    \end{cases}


均值池化
=============

一维
-------------

.. math:: O(m) = \sum\limits_{i=m}^{w+m} I(i) K(i)

.. math:: k(i) = \frac{1}{w}

二维
----------

.. math:: O(m,n) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n} I(i,j) K(i,j)

.. math:: k(i,j) = \frac{1}{w \times h}

三维
---------

.. math:: O(m,n) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n} \sum\limits_{k=z}^{l+z} I(i,j,k) K(i,j,k)

.. math:: k(i,j,k) = \frac{1}{w \times h \times l}


高效实现
*************

