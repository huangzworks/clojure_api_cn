.. _deref:

deref
=======

| **(deref ref)**
| **(deref ref timeout-ms timeout-val)**

``deref`` 等同于这些读入器宏(reader macro)： ``@ref`` / ``@agent`` / ``@var`` / ``@atom`` / ``@delay`` / ``@future`` / ``@promise`` 。

在事务中调用 ``deref`` 时，返回 ``ref`` 的事务值(in-transaction-value)；在非事务情况下调用，则返回 ``ref`` 的最近一次提交值(most-recently-committed value).

应用于 ``var`` 、 ``agent`` 或 ``atom`` 时，返回它们的当前状态。

应用于 ``future`` 时，如果计算尚未完成，那么阻塞。

应用于 ``promise`` 时，如果该 ``promise`` 还没用 ``deliver`` 设置过值，那么阻塞。

带 ``timeout`` 参数的变种(variant)用于处理 ``future`` 和 ``promise`` 这种可能会阻塞的引用(reference)：当阻塞时长超过 ``timeout`` 毫秒，而引用还未有值可用时，返回 ``timeout-val`` 作为值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L2067>`_

::

    ; 普通的 deref

    user=> (def d (delay (+ 1 1)))
    #'user/d

    user=> (deref d)
    2

    user=> @d
    2

    ; 带超时的 deref

    user=> (def p (promise))
    #'user/p

    user=> (deref p 5000 nil)   ; 5 秒内没有可用值，就返回 nil
    nil

