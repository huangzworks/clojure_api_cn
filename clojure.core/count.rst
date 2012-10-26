count
----------

**(count coll)**

返回 ``coll`` 中元素的数量。

``(count nil)`` 返回 ``0`` 。

``coll`` 也可以是字符串、数组、Java Collection 和 Map 。

::

    user=> (count nil)
    0

    user=> (count [1 2 3 4])
    4

    user=> (count (list 1 2 3 4))
    4

    user=> (count "string")
    6

    user=> (count {:clojure "Rich" :python "Guido" :ruby :Matz})
    3


