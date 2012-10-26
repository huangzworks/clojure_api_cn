constantly
------------

**(constantly x)**

返回一个匿名函数，
接受任何数量的参数，
但总是返回 ``x`` 。

::

    user=> (def ten (constantly 10))
    #'user/ten

    user=> (ten)
    10

    user=> (ten 1)
    10

    user=> (ten 1 2)
    10

    user=> (ten 1 2 3)
    10



