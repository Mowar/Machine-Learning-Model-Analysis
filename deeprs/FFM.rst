FFM(field-aware factorization machines)
#############################################

表达式
==========

字段越多,相对于FM更加难以学习

归一化影响
============
we find that normalizing each instance to have the
unit length makes the test accuracy slightly better
and insensitive to parameters.


coded information
===================

categorical feature
***********************

numerical features
************************

Single-field Features
***********************

scene
===========================

- FFMs should be effective for data sets that contain categorical features and are transformed to binary features.

- If the transformed set is not sparse enough, FFMs seem to bring less benefit

- It is more difficult to apply FFMs on numerical data sets.