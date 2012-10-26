cons
---------

**(cons x seq)**

返回一个新的序列，
序列的第一个元素是 ``x`` ，
而 ``seq`` 则是序列的其余部分。

::

    ; cons 起数字 1 和空列表

    user=> (cons 1 '())
    (1)


    ; cons 起数字 1 和列表 (2 3)

    user=> (cons 1 (list 2 3))
    (1 2 3)



