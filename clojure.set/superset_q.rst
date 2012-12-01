superset?
===========

| **(superset? set1 set2)**

判断 ``set1`` 是否 ``set2`` 的超集。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L150>`_

::

    user> (clojure.set/superset? #{:a :b :c} #{:a :b})
    true

    user> (clojure.set/superset? #{:a :c :d} #{:a :b})
    false

    user> (clojure.set/superset? #{:a :b} #{:a :b})
    true

    user> (clojure.set/superset? #{:a :b} #{})
    true
