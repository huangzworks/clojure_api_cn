.. _promise:

promise
=========

**(promise)**

*试验版本，将来可能会出现改动。*

返回一个 ``promise`` 对象，可以使用 ``deref`` 或者 ``@`` 读取它的值，也可以使用 ``deliver`` 对它进行只能设置一次的赋值。

如果 ``promise`` 对象在使用 ``deliver`` 设置值之前，就被 ``deref`` 或者 ``@`` 读取，那么调用者将被阻塞，直到 ``promise`` 对象有值，或者 ``deref`` 设置的超时时间到期为止。

被 ``deliver`` 设置值之后，对 ``promise`` 的每次 ``deref`` 或者 ``@`` 都会不阻塞地返回 ``deliver`` 所设置的值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6278>`_

::

    user=> (def p (promise))
    #'user/p

    user=> p
    #<core$promise$reify__6153@bfb588: :pending>

    ; 对未有值的 promise 进行 deref
    ; 为了避免陷入无限阻塞，设置 5 秒的超时时间

    user=> (deref p 5000 "reach timeout")
    "reach timeout"

    ; 为 promise 设置值

    user=> (deliver p 10086)
    #<core$promise$reify__6153@bfb588: 10086>

    user=> @p
    10086

    user=> p
    #<core$promise$reify__6153@bfb588: 10086>

    ; 试试重复 deliver ？

    user=> (deliver p 123123)
    nil

    user=> @p
    10086
