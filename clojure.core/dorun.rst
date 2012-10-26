dorun
---------

| **(dorun coll)**
| **(dorun n coll)**

对于那些带副作用的函数所生成的惰性序列来说，只有当列表的某个元素被求值时，该元素的副作用才会被显现出来。

``dorun`` 使用 ``next`` 函数遍历整个序列，从而迫使惰性列表的副作用产生。

这个函数返回 ``nil`` ，而不是序列的首个元素。

自 Clojure 1.0 版本以来可用。

::

    user=> (def infinity-hi (repeatedly #(println "hi")))
    #'user/infinity-hi

    user=> (dorun 5 infinity-hi)
    hi
    hi
    hi
    hi
    hi
    hi
    nil

    user=> (def one-to-ten (map println (range 10)))
    #'user/one-to-ten

    user=> (dorun one-to-ten)
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    nil
