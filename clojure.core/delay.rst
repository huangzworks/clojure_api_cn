delay
======

**(delay & body)**

参数 ``body`` 接受一系列表达式，并返回一个 ``Delay`` 对象。

这个 ``Delay`` 对象只有在第一次被 ``force`` 函数、 ``deref`` 函数或者 ``@`` 宏强迫求值时，才会对 ``body`` 进行求值。

``body`` 的求值结果会被缓存，之后对这个 ``Delay`` 对象的所有强迫求值，都返回这个缓存结果。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L682>`_

::

    user=> (def d (delay (println "force delay object") 
                         (+ 1 1)))
    #'user/d

    user=> d
    #<Delay@15c5bba: :pending>

    user=> @d
    force delay object      ; 第一次强迫求值
    2                       ; 这个值会被缓存

    user=> @d
    2                       ; 不再求值 body ，只返回缓存值

    user=> d   
    #<Delay@15c5bba: 2>     ; 打印值现在带有 body 的值
