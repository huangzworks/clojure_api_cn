doall
---------

| **(doall coll)**
| **(doall n coll)**


对于那些带副作用的函数所生成的惰性序列来说，只有当列表的某个元素被求值时，该元素的副作用才会被显现出来。

``doall`` 使用 ``next`` 函数遍历整个序列，从而迫使惰性序列的副作用产生。

这个函数返回序列的首个元素作为结果，因此它需要在内存中保存整个序列。

自 Clojure 1.0 以来可用。

::

    user=> (def one-to-three (range 3))
    #'user/one-to-three

    user=> (doall one-to-three)
    (0 1 2)

    user=> one-to-three
    (0 1 2)

