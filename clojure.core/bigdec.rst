bigdec
--------

**(bigdec x)**


将 ``x`` 强制转换为 ``BigDecimal`` 

`查看源码 <https://github.com/clojure/clojure/blob/c6756a8bab137128c8119add29a25b0a88509900/src/clj/clojure/core.clj#L3295>`_


::

        user=> (bigdec 3.0)
        3.0M

        user=> (bigdec 5)
        5M

        user=> (bigdec -1)
        -1M

        user=> (bigdec -1.0)
        -1.0M


