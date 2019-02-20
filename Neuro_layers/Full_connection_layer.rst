Full connection layer
########################

图例
********************

表达式
****************

一维(向量)
==================

.. math:: O(n) = \sum\limits_{i=1}^{x}I(i)K(i)_n

.. math:: \frac{\partial{O(n)}}{\mathrm{d}K_n} = I

二维(矩阵)
==================

.. math:: O(n) = \sum\limits_{i=1}^{x}\sum\limits_{j=1}^{y} I(i,j)K(i,j)_n

.. math::  \frac{\partial{O(n)}}{\mathrm{d}K_n} = I

三维(张量)
===================

.. math:: O(n) = \sum\limits_{i=1}^{x}\sum\limits_{j=1}^{y} \sum\limits_{k=1}^{z}I(i,j,k)K(i,j,k)_n

.. math:: \frac{\partial{O(n)}}{\mathrm{d}K_n} = I

高效实现
**************

