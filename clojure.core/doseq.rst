doseq
----------

| **(doseq seq-exprs & body)**

使用和 ``for`` 宏一样的绑定和过滤器，反复执行 ``body`` （通常是为了产生副作用）。

返回 ``nil`` 而不是序列的首元素作为函数结果。

自 Clojure 1.0 版本以来可用。

::

    user=> (doseq [i (range 10)] (prn i))
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
