delay?
=======

**(delay? x)**

如果 ``x`` 是用 ``delay`` 创建的一个 ``Delay`` 对象，那么返回 ``true`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L691>`_

::

    user=> (delay? 2)
    false

    user=> (delay? (delay))
    true
