first
---------

**(first coll)**

返回 ``coll``  中的第一个元素。

传入的 ``coll`` 会被 ``seq`` 函数处理。

如果 ``coll`` 为 ``nil`` ，返回 ``nil`` 。

::

    user=> (first nil)
    nil

    user=> (first [1 2 3])
    1

    user=> (first (list 1 2 3))
    1

    user=> (first {:clojure "Rich" :python "Guido" :ruby "Matz"})
    [:python "Guido"]


