complement
--------------

**(complement f)**

接受一个函数 ``f`` ，返回一个匿名函数。

这个匿名函数接受的参数、产生的作用都和 ``f`` 一样，
但它返回的真值和 ``f`` 相反。

::

    user=> (defn f []
               (println "hello")
               false)
    #'user/f

    user=> (f)
    hello
    false

    user=> ((complement f))
    hello
    true


