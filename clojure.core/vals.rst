vals
---------

**(vals map)**

返回一个序列，序列里包含给定 ``map`` 的所有值(value)。

::

    ; 空 Map

    user=> (vals {})
    nil

    ; 非空 Map

    user=> (vals {:python "Guido" :clojure "Rich" :ruby "Matz"})
    ("Guido" "Matz" "Rich")


