range
---------

| **(range)**
| **(range end)**
| **(range start end)**
| **(range start end step)**

返回一个惰性序列，
序列里包含从大于等于 ``start`` 到小于 ``end`` 
区间内的所有数字(``start <= numbers < end``)，
数字的步进以 ``step`` 指定。

默认情况下， ``start`` 为 ``0`` ， ``step`` 为 ``1`` ，而 ``end`` 则为无限。

::

    ; 不指定任何参数，返回一个包含所有非负整数的惰性序列
    ; 0, 1, 2, 3 ...

    user=> (take 3 (range))
    (0 1 2)

    user=> (take 10 (range))
    (0 1 2 3 4 5 6 7 8 9)


    ; 只指定 end 
    ; 返回大于等于 0 到小于 end 之内的所有整数

    user=> (range 5)
    (0 1 2 3 4)

    user=> (range 10)
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 和 end

    user=> (range 5 10)
    (5 6 7 8 9)

    user=> (range 0 10)   
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 、 end 和 step
    ; 第一个惰性序列计算 2 到 20 内的所有偶数
    ; 第二个惰性序列计算 1 到 20 内的所有奇数

    user=> (range 2 20 2)
    (2 4 6 8 10 12 14 16 18)

    user=> (range 1 20 2)
    (1 3 5 7 9 11 13 15 17 19)

