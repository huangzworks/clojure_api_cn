subset?
=========

| **(subset? set1 set2)**

判断 ``set1`` 是否是 ``set2`` 的子集

::

    user> (clojure.set/subset? #{:a :b} #{:a :b :c})
    true
    user> (clojure.set/subset? #{:a :b} #{:a :c :d})
    false
    user> (clojure.set/subset? #{} #{:a :c :d})
    true
    user> (clojure.set/subset? #{:a} #{:a})
    true
