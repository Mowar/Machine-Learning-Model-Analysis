convolution layer
####################

图例
*******

表达式
********

一维
============

.. math:: O(n) = \sum\limits_{i=n}^{w+n}I(i)K(i)

.. math:: \frac{\partial{O(n)}}{\mathrm{d}K} = I[n:w+n]

总梯度
+++++++++++

.. math:: \frac{\partial{ (\sum\limits_{n=0}^{N}O(n)})}{\mathrm{d}K} = \sum\limits_{n=0}^{o} I[n:w+n]

二维
============

.. math:: O(m,n) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n} I(i,j)K(i,j)

.. math:: \frac{\partial{O(m,n)}}{\mathrm{d}K} = I[m:w+m;n:h+n]

总梯度
+++++++++++

.. math:: \frac{\partial{(\sum\limits_{m=0}^{M}\sum\limits_{n=0}^{N} O(m,n))}}{\mathrm{d}K} = \sum\limits_{m=0}^{M}\sum\limits_{n=0}^{N} I[m:w+m;n:h+n]

三维
=============

.. math::  O(m,n,v) = \sum\limits_{i=m}^{w+m}\sum\limits_{j=n}^{h+n}\sum\limits_{k=v}^{l+v} I(i,j,k)K(i,j,k)

.. math:: \frac{\partial{O(m,n,v)}}{\mathrm{d}K} = I[m:w+m;n:h+n;v:l+v]

总梯度
++++++++++

.. math:: \frac{\partial{(\sum\limits_{m=0}^{M}\sum\limits_{n=0}^{N} \sum\limits_{v=0}^{V} O(m,n,v))}}{\mathrm{d}K} = \sum\limits_{m=0}^{M}\sum\limits_{n=0}^{N}\sum\limits_{v=0}^{V} I[m:w+m;n:h+n;v:l+v]


.. Warning:: 相关梯度的计算有待查阅

高效实现
**********
