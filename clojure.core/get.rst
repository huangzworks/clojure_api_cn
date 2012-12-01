get
====

| **(get map key)**
| **(get map key not-found)**

返回 ``map`` 中 ``key`` 所映射的值。

如果该 ``key`` 不存在，且给定了 ``not-found`` ，那么返回 ``not-found`` ，否则，返回 ``nil`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L1388>`_

::

    user=> (def clojure {:author "Rich Hickey"})
    #'user/clojure

    user=> (get clojure :author)
    "Rich Hickey"

    user=> (get clojure :version)       ; 无 not-found 参数
    nil

    user=> (get clojure :version 1.4)   ; 有 not-found 参数
    1.4

