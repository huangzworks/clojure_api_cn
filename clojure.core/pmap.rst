pmap
=======

| **(pmap f coll)**
| **(pmap f coll & colls)**

``pmap`` 类似于 ``map`` ，唯一的不同是， ``pmap`` 对函数 ``f`` 的应用是并行的。

``pmap`` 的返回值是半惰性的(semi-lazy)：
并行计算总是发生在消耗(consumption)之前，
不过，计算结果只有在被需要时，才会被 realize 。

只有当 ``f`` 为计算密集型函数，
而且并行获得的性能提升足以抵消并行所需的协调消耗时，
才应该使用 ``pmap`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6194>`_

::

    ; 串行运行， 4 个元素，每个等待 3 秒，共等待 12 秒
    user=> (time
             (dorun
               (map (fn [x] (Thread/sleep 3000))
                    (range 4))))
    "Elapsed time: 12000.767484 msecs"
    nil

    ; 并行运行， 4 个元素，每个等待 3 秒，共等待 3 秒
    user=> (time
             (dorun
               (pmap (fn [x] (Thread/sleep 3000))
                     (range 4))))
    "Elapsed time: 3002.602211 msecs"
    nil
