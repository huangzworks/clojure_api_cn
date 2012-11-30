superset?
===========

| **(superset? set1 set2)**

判断 ``set1`` 是否是 ``set2`` 的超集。

::

    user> (clojure.set/superset? #{:a :b :c} #{:a :b})
    true
    user> (clojure.set/superset? #{:a :c :d} #{:a :b})
    false
    user> (clojure.set/superset? #{:a :b} #{:a :b})
    true
    user> (clojure.set/superset? #{:a :b} #{})
    true
