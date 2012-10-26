filter
--------

**(filter pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``true`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 过滤 0 - 9 中所有的奇数

    user=> (filter even? (range 10))
    (0 2 4 6 8)


    ; 过滤 0 - 9 中所有的偶数

    user=> (filter odd? (range 10))
    (1 3 5 7 9)


    ; 过滤 0 - 9 中所有小于 10086 的数，结果为空

    user=> (filter #(> % 10086) (range 10))
    ()



