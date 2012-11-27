realized?
===========

**(realized? x)**

如果给定的 ``promise`` 、 ``delay`` 、 ``future`` 或者 ``lazy-list`` 对象已经有值了，那么返回 ``true`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6604>`_

::

    user=> (def d (delay (+ 1 1)))
    #'user/d

    user=> (realized? d)
    false

    user=> @d
    2

    user=> (realized? d)
    true
