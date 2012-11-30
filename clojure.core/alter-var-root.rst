alter-var-root
=====================

**(alter-var-root v f & args)**

原子性地修改 var ``v`` 的值，新值由 ``v`` 的旧值和给定的 ``args`` 应用到函数 ``f`` 得出。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L4834>`_

::

    user=> (def v 10)
    #'user/v

    user=> (alter-var-root (var v) + 1)     ; (var v) 等同于 #'v
    11

    user=> v
    11
