intersection
================

| **(intersection s1)**
| **(intersection s1 s2)**
| **(intersection s1 s2 & sets)**

计算输入集合的交集。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L32>`_

::

    user> (use 'clojure.set)
    nil

    user> (intersection #{1 2 3} #{3 4 5})
    #{3}

    user> (intersection #{1 2 3} #{2 3} #{3})
    #{3}
