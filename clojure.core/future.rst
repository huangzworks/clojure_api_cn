.. _future:

future
=========

**(future & body)**

参数 ``body`` 接受一系列表达式，并返回一个 ``future`` 对象，使用 ``deref`` 或者 ``@`` 可以对这个对象进行强迫求值。

``future`` 对象会在另一个线程里对 ``body`` 进行求值，并将求值结果保存到缓存中，之后对这个 ``future`` 对象的所有强迫求值都会返回这个缓存值。

如果强迫求值时 ``body`` 的计算还没完成，那么调用者将被阻塞，直到计算完成，或者 ``deref`` 设置的过期时间到达为止。

::

    ; 普通的 future 调用

    user=> (def f (future (+ 1 1)))
    #'user/f

    user=> f
    #<core$future_call$reify__6110@fae040: 2>

    user=> @f
    2

    ; 一个停滞 5 秒的 future 调用

    user=> @(future (println "start sleep") (Thread/sleep 5000) 10086)
    start sleep
    10086

    ; 一个带 timeout 的 deref 调用的例子，防止阻塞时间过长

    user=> (deref (future (Thread/sleep 10000000000000000))
                  1000
                  "reach block timeout") ; 停滞 1 秒之后返回字符串值
    "reach block timeout"
