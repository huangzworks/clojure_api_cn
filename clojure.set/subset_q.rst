subset?
=========

| **(subset? set1 set2)**

判断 ``set1`` 是否 ``set2`` 的子集。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L142>`_

::

    user> (clojure.set/subset? #{:a :b} #{:a :b :c})
    true

    user> (clojure.set/subset? #{:a :b} #{:a :c :d})
    false

    user> (clojure.set/subset? #{} #{:a :c :d})
    true

    user> (clojure.set/subset? #{:a} #{:a})
    true
