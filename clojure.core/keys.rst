keys
---------

**(keys map)**

返回一个序列，序列里包含给定 ``map`` 的所有键(key)。

::

    ; 空 Map

    user=> (keys {})
    nil

    ; 非空 Map

    user=> (keys {:python "Guido" :clojure "Rich" :ruby "Matz"})
    (:python :ruby :clojure)


