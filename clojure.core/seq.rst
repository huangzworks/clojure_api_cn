seq
------

**(seq coll)**

根据给定的 ``coll`` ，返回一个相应的序列。

当 ``coll`` 为空时，返回 ``nil`` 。

``(sql nil)`` 也返回 ``nil`` 。

``seq`` 函数也可以作用于字符串、
（带有引用类型的）原生 Java 数组，
以及任何实现了 ``iterable`` 接口的对象。

::

    ; 处理空向量和 nil

    user=> (seq [])
    nil

    user=> (seq nil)
    nil

    ; 处理非空向量、列表、 Map 和字符串

    user=> (seq [1 2 3])
    (1 2 3)

    user=> (seq (list 1 2 3))
    (1 2 3)

    user=> (seq {:language "clojure" :creator "Rich Hickey"})
    ([:creator "Rich Hickey"] [:language "clojure"])

    user=> (seq "hello world")
    (\h \e \l \l \o \space \w \o \r \l \d)
