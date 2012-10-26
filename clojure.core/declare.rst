declare
-----------

**(declare & names)**

定义一些无绑定的 var 名字，用于提前声明（forward declarations）。

::

    user=> (defn f []
               (g))
    ;CompilerException java.lang.RuntimeException: Unable to resolve symbol: g in this context, compiling:(NO_SOURCE_PATH:2) 

    user=> (declare g)
    #'user/g

    user=> (defn f []
                (g))
    #'user/f
