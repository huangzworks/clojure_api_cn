next
--------

**(next coll)**

返回 ``coll`` 除了第一个元素之外，余下的其他全部元素。

传入的 ``coll`` 会被 ``seq`` 函数处理。

如果 ``coll`` 除了 ``(first coll)`` 之外，
没有其他别的元素，那么返回 ``nil`` 。

::

    user=> (next nil)
    nil

    user=> (next [1])
    nil

    user=> (next [1 2])
    (2)

    user=> (next [1 2 3])
    (2 3)


