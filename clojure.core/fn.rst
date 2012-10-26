fn
----

| **params => positional-params\*** 或者 **positional-params\* & next-param**
| **positional-param => binding-form**
| **next-param => binding-form**
| **name => symbol**

定义一个（匿名）函数。

::

    user=> (fn greeting [name]                                          ; 创建匿名函数
               (str "Hello, " name " ."))
    ;#<user$eval1$greeting__2 user$eval1$greeting__2@616fde>

    user=> ((fn greeting [name]                                         ; 应用匿名函数
               (str "hello, " name " ."))
            "moto")
    "hello, moto ."

    user=> ((fn greeting                                                ; 参数重载（arity overloading）
                ([name]    
                    (greeting "Hello" name))
                ([msg name]
                    (str msg ", " name " .")))
            "moto")
    "Hello, moto ."

    user=> ((fn greeting                                                ; 接受不定数量参数的函数
                [name & others]
                (if (seq others)
                    (str "Hello, " name " and others: " others " .")
                    (str "Hello, " name " .")))
            "moto" "nokia" "apple")      
    "Hello, moto and others: (\"nokia\" \"apple\") ."


