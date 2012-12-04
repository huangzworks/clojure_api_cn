mapcat
========

**(mapcat f & colls)**

等同于调用 ``(concat (map f colls))`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L2455>`_

::

    user=> (mapcat reverse [[3 2 1 0] 
                            [6 5 4]
                            [9 8 7]])
    (0 1 2 3 4 5 6 7 8 9)

