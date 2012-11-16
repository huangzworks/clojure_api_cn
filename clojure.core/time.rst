time
------

**(time expr)**

对 ``expr`` 进行求值，并打印求值所花费的时间。

``expr`` 的值作为函数的返回值被返回。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L3424>`_

::

    ; 计算对比两个关键字 100 次所需的时间

    user=> (time 
             (dotimes [_ 100] 
               (= :kw :kw)))
    "Elapsed time: 0.23802 msecs"
    nil
