letfn
----------

| **(letfn fnspecs & body)**

| **fnspecs ==> (fname [params*] exprs)** 或者 **(fname ([params*] exprs)+)**

使用一个函数体 ``body`` ，以及一个带有函数规格(specs)的向量 ``fnspecs`` ，
将向量里的名字和相应的函数进行绑定。

向量里的名字在函数定义中，还有函数体内，都是可见的。

::

    user=> (letfn [(twice [x]
                      (* x 2))
                   (six-times [y]
                      (* 3 (twice y)))]
               (println "Twice 15 = " (twice 15))
               (println "Six times 15 = " (six-times 15)))
    Twice 15 = 30 
    Six times 15 = 90 
    nil 

    ;; 名字 twice 和 six-times 在离开 letfn 之后不可用

    ;user=> (twice 15)   
    ;CompilerException java.lang.RuntimeException: Unable to resolve symbol: twice in this context, compiling:(NO_SOURCE_PATH:7) 

    ;user=> (six-times 15) 
    ;CompilerException java.lang.RuntimeException: Unable to resolve symbol: six-times in this context, compiling:(NO_SOURCE_PATH:8)


