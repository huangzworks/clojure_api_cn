defonce
-----------

**(defonce name expr)**

将 ``name`` 的 root value 设置为 ``expr`` 的值，当且仅当 ``name`` 还没有设置 root value 。

如果 ``name`` 已经有 root value ，那么 ``expr`` 不会被求值。


::

    user=> number                       ; 没有 root value
    ;CompilerException java.lang.RuntimeException: Unable to resolve symbol: number in this context, compiling:(NO_SOURCE_PATH:0) 

    user=> (defonce number 10086)       ; 设置 root value
    #'user/number

    user=> number
    10086

    user=> (defonce number 123123)      ; 已有 root value ，设置失败
    nil

    user=> number
    10086
