pvalues
============

| **(pvalues & exprs)**

并行计算 ``exprs`` 中的表达式，并以惰性序列的形式返回它们的值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6226>`_

::

    user=> (pvalues 
             (Thread/sleep 3000)
             10086
             (Thread/sleep 3000)
             "hello moto")
    (nil 10086 nil "hello moto")    ; 返回完整的计算结果需要 3 秒时间

.. include:: problem-of-pcalls-and-pvalues.rst
