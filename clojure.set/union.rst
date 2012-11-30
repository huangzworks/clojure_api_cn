union
===========

| **(union)**
| **(union s1)**
| **(union s1 s2)**
| **(union s1 s2 & sets)**

返回输入集合的并集。

::

    user> (clojure.set/union)
    #{}
    user> (clojure.set/union #{:a} #{:b :c})
    #{:a :c :b}
    user> (clojure.set/union #{:a :b} #{:b :c})
    #{:a :c :b}
