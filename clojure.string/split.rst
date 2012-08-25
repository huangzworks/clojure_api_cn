split
-------

| **(split s re)**
| **(split s re limit)**

根据正则表达式 ``re`` ，对字符串 ``s`` 进行分割，结果所得的一个或多个字符串保存在一个向量里面。

可选的 ``limit`` 参数指定最大的分割次数。

这个函数不是惰性的。

::

    ; 分割 #"\r?\n" 是 clojure.string/split-lines 的定义

    user=> (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n")
    ["hello" "moto" "again"]

    ; 带 limit 参数

    user=> (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n" 1)
    ["hello\nmoto\r\nagain\r\n"]

    user=>  (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n" 2)
    ["hello" "moto\r\nagain\r\n"]

    user=>  (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n" 3)
    ["hello" "moto" "again\r\n"]

    user=>  (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n" 4)
    ["hello" "moto" "again" ""]

    user=>  (clojure.string/split "hello\nmoto\r\nagain\r\n" #"\r?\n" 5)
    ["hello" "moto" "again" ""]
