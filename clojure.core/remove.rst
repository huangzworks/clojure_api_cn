remove
----------

**(remove pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``false`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 删除 0 - 9 中的所有偶数

    user=> (remove even? (range 10))
    (1 3 5 7 9)


    ; 删除 0 - 9 中的所有奇数

    user=> (remove odd? (range 10))
    (0 2 4 6 8)


    ; 删除 0 - 9 中所有大于等于 0 的数字，结果为空

    user=> (remove #(>= % 0) (range 10)) 
    ()


