union
===========

| **(union)**
| **(union s1)**
| **(union s1 s2)**
| **(union s1 s2 & sets)**

返回输入集合的并集。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L19>`_

::

    user> (clojure.set/union)
    #{}

    user> (clojure.set/union #{:a} #{:b :c})
    #{:a :c :b}

    user> (clojure.set/union #{:a :b} #{:b :c})
    #{:a :c :b}
