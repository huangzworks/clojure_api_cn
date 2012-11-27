pcalls
=======

**(pcalls & fns)**

并行计算 ``fns`` 中的无参数函数，并以惰性序列的形式返回它们的值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6219>`_

::

    ; 并行运行 3 个等待 3 秒的线程，共等待 3 秒
    user=> (pcalls
             #(Thread/sleep 3000)
             #(Thread/sleep 3000)
             #(Thread/sleep 3000))
    (nil nil nil)

.. include:: problem-of-pcalls-and-pvalues.rst
