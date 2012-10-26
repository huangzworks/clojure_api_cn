empty?
----------

**(empty? coll)**

如果 ``coll`` 中不包含任何元素，那么返回 ``true`` ，
效果等同于执行 ``(not (seq coll))`` 。

请使用惯用法 ``(seq x)`` 代替 ``(not (empty? x))`` 。

::

    user=> (empty? '())
    true

    user=> (empty? nil)
    true

    user=> (empty? [1 2 3])
    false


