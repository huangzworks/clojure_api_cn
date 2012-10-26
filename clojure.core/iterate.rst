iterate
--------

| **(iterate f x)**

返回一个惰性序列，
序列元素的值为 ``x`` 、 ``(f x)`` 、 ``(f (f x))`` 、 ``(f (f (f x)))`` ，
诸如此类。

函数 ``f`` 必须是无副作用的。

::

    ; 生成一个计算所有正整数的惰性序列

    user=> (def z (iterate inc 1))
    #'user/z


    ; 取出第一个和第二个正整数

    user=> (nth z 0)
    1

    user=> (nth z 1)
    2


    ; 取出前十个正整数

    user=> (take 10 z)
    (1 2 3 4 5 6 7 8 9 10)


