map-invert
============


| **(map-invert m)**

转置一个map，把value作为key，把key作为value。
小心：当多个key有同一个value时，只保留一个key。

p.s. 为毛这个函数在clojure.set里头...

::

    user> (use 'clojure.set)
    nil
    user> (map-invert {:a 1 :b 2})
    {2 :b, 1 :a}
    user> (map-invert {:a 1 :b 2 :c 2}) ;; 丢掉了:c
    {2 :b, 1 :a}
