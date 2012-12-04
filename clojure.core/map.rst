map
=====

| **(map f coll)**
| **(map f c1 c2)**
| **(map f c1 c2 c3)**
| **(map f c1 c2 c3 & colls)**

返回一个惰性序列，
序列的第一个元素是所有给定 ``collection`` 的第一个元素应用于函数 ``f`` 所得出的返回值，
序列的第二个元素是所有给定 ``collection`` 的第二个元素应用于函数 ``f`` 所得出的返回值。。。以此类推，一直到给定 ``collection`` 的其中一个被处理完为止。

当其中一个 ``collection`` 被处理完之后，其他 ``collection`` 的剩余元素会被忽略，因此结果序列的长度由给定 ``collection`` 中长度最短的那个决定。

函数 ``f`` 的参数个数应该和给定 ``collection`` 的数量一致。

`查看源码 <http://clojure.github.com/clojure/clojure.core-api.html#clojure.core/map>`_

::

    ;; 处理单个 collection

    user=> (range 10)
    (0 1 2 3 4 5 6 7 8 9)

    user=> (map inc (range 10))
    (1 2 3 4 5 6 7 8 9 10)


    ;; 处理两个 collection

    user=> (range 0 10)
    (0 1 2 3 4 5 6 7 8 9)

    user=> (reverse (range 0 10))
    (9 8 7 6 5 4 3 2 1 0)

    user=> (map #(+ %1 %2) (range 10) (reverse (range 10)))
    (9 9 9 9 9 9 9 9 9 9)


    ;; 处理长度不同的两个 collection

    user=> (map #(+ %1 %2) (range 10086) (reverse (range 10)))
    (9 9 9 9 9 9 9 9 9 9)

