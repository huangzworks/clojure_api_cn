cond
---------

**(cond & clauses)**

接受一系列 ``test``/``expression`` 对，
它每次对一个 ``test`` 进行求值，
如果某个 ``test`` 返回 ``true`` ，
那么 ``cond`` 求值并返回与这个 ``test`` 相对应的 ``expression`` ，
并且不再对其他 ``test`` 进行求值。

``(cond)`` 返回 ``nil`` 。

::

    user=> (defn type-of-number [n]
               (cond (> n 0) "positive number"
                     (< n 0) "negative number"
                     :else "zero"))
    #'user/type-of-number

    user=> (type-of-number 10)
    "positive number"

    user=> (type-of-number -5)
    "negative number"

    user=> (type-of-number 0)
    "zero"



