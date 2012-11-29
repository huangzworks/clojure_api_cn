intersection
--------

| **(intersection s1)**
| **(intersection s1 s2)**
| **(intersection s1 s2 & sets)**

计算输入集合的交集。

::

    user> (use 'clojure.set)
    nil
    user> (intersection #{1 2 3} #{3 4 5})
    #{3}
    user> (intersection #{1 2 3} #{2 3} #{3})
    #{3}
