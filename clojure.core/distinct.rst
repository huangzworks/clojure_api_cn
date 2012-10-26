distinct
----------

**(distinct coll)**

给定一个 ``coll`` ，返回一个无重复元素的惰性序列。

::

    ; 有重复元素的向量

    user=> (distinct [1 2 1 2])
    (1 2)

    
    ; 无重复元素的向量

    user=> (distinct [1 2 3 4])
    (1 2 3 4)


