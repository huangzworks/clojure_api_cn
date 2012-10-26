repeatedly
-----------------

| **(repeatedly f)**
| **(repeatedly n f)**

给定一个无参数的函数 ``f`` (通常带有副作用)，返回一个调用 ``f`` 函数 ``n`` 次的惰性序列。

如果不指定参数 ``n`` ，那么函数 ``f`` 可以执行无限次。

::

    ; 测试函数

    user=> (defn greet []                     
             "hi!")       
    #'user/greet


    ; 定义一个执行 10 次 greet 的惰性序列
    ; 并用 take 函数取出 5 个和 10 个 greet 的执行结果

    user=> (def ten-greet (repeatedly 10 greet))
    #'user/ten-greet

    user=> (take 5 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!")

    user=> (take 10 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")


    ; 试图取出 10086 个值，但 ten-greet 最多只返回 10 个值
    ; 说明取出的数量最多只能和 n 一样大

    user=> (take 10086 ten-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")


    ; 定义一个执行无限次 greet 的惰性序列

    user=> (def infinite-greet (repeatedly greet))
    #'user/infinite-greet

    user=> (take 10 infinite-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")

    user=> (take 100 infinite-greet)
    ("hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!" "hi!")



