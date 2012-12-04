reductions
============

| **(reductions f coll)**
| **(reductions f init coll)**

返回一个惰性序列，
序列里包含计算 ``(reduce f coll)`` 所产生的所有中间结果。

如果给定了 ``init`` ，那么将它用作所有中间结果的初始值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6368>`_

::

    user=> (reduce + (range 1 10))
    45

    user=> (reductions + (range 1 10))
    (1 3 6 10 15 21 28 36 45)

    user=> (reductions + 0 (range 1 10))    ; 注意 init 不止添加到序列头那么简单
    (0 1 3 6 10 15 21 28 36 45)

    user=> (reductions + 10 (range 1 10))   ; 它还作为每个中间值的初始化值
    (10 11 13 16 20 25 31 38 46 55)
