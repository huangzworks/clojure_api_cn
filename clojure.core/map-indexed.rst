map-indexed
==============

| **(map-indexed f coll)**

返回一个惰性序列，
序列里的第一个元素是将 ``0`` 和 ``coll`` 的第一个元素应用到 ``f`` 所得出的值，
序列里的第二个元素是将 ``1`` 和 ``coll`` 的第二个元素应用到 ``f`` 所得出的值。。。
以此类推，直到 ``coll`` 被处理完为止。

函数 ``f`` 应该接受两个参数：一个索引值，一个是 ``coll`` 的元素值。

`查看源码 <http://clojure.github.com/clojure/clojure.core-api.html#clojure.core/map-indexed>`_

::

    user=> (map-indexed (fn [idx item] [idx item]) "foobar")
    ([0 \f] [1 \o] [2 \o] [3 \b] [4 \a] [5 \r])

    user=> (map-indexed vector "foobar")    ; 另一种更简单的解法
    ([0 \f] [1 \o] [2 \o] [3 \b] [4 \a] [5 \r])

