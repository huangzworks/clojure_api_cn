when-not
----------

**(when-not test & body)**

对 ``test`` 部分进行求值，如果结果为 ``false`` ，那么在一个隐式 ``do`` 的包围下对 ``body`` 进行求值。

::

    user=> (when-not true
               (println "hello")
               (println "moto"))
    nil

    user=> (when-not false
               (println "hello")
               (println "moto"))
    hello
    moto
    nil
