clojure.core
=================

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

    ; 处理非空向量、列表、 map 和字符串

    user=> (seq [1 2 3])
    (1 2 3)

    user=> (seq (list 1 2 3))
    (1 2 3)

    user=> (seq {:language "clojure" :creator "Rich Hickey"})
    ([:creator "Rich Hickey"] [:language "clojure"])

    user=> (seq "hello world")
    (\h \e \l \l \o \space \w \o \r \l \d)


vals
---------

**(vals map)**

返回一个序列，序列里包含给定 ``map`` 的所有值(value)。

::

    ; 空 map

    user=> (vals {})
    nil

    ; 非空 map

    user=> (vals {:python "Guido" :clojure "Rich" :ruby "Matz"})
    ("Guido" "Matz" "Rich")


keys
---------

**(keys map)**

返回一个序列，序列里包含给定 ``map`` 的所有键(key)。

::

    ; 空 map

    user=> (keys {})
    nil

    ; 非空 map

    user=> (keys {:python "Guido" :clojure "Rich" :ruby "Matz"})
    (:python :ruby :clojure)


rseq
---------

**(rseq rev)**

在常数时间内，返回 ``rev`` 的逆序序列。

``rev`` 只能是向量或者 sorted-map 。

``rev`` 为空时，返回 ``nil`` 。

::

    ; 空向量和空 sorted-map

    user=> (rseq [])
    nil

    user=> (rseq (sorted-map))
    nil


    ; 非空向量

    user=> (rseq [1 2 3])
    (3 2 1)


    ; 非空 sorted-map

    user=> (def alpha (sorted-map :a "apple" :b "boy" :c "cat"))
    #'user/alpha

    user=> alpha
    {:a "apple", :b "boy", :c "cat"}

    user=> (rseq alpha)
    ([:c "cat"] [:b "boy"] [:a "apple"])


    ; 一些不能处理的情况

    user=> (rseq (list 1 2 3))
    ClassCastException clojure.lang.PersistentList cannot be cast to clojure.lang.Reversible  clojure.core/rseq (core.clj:1480)

    user=> (rseq nil)
    NullPointerException   clojure.core/rseq (core.clj:1480)


subseq
---------

| **(subseq sc test key)**
| **(subseq sc start-test start-key end-test end-key)**

过滤 ``sc`` 并返回一个序列，序列里的所有实体(entry)的键 ``ek`` 都必须符合条件 ``(true? (test (.. sc comparator (compare ek key)) 0))`` 。

如果没有任何实体符合条件，则返回 ``nil`` 。

参数 ``sc`` 必须是一个 sorted collection ，测试条件 ``test`` 可以是 ``<`` 、 ``<=`` 、 ``>`` 或者 ``>=`` 。

::

    ; 测试数据

    user=> (def numbers (sorted-map 1 "one" 2 "two" 3 "three" 4 "four" 5 "five"))
    #'user/numbers

    user=> numbers
    {1 "one", 2 "two", 3 "three", 4 "four", 5 "five"}


    ; 过滤所有键小于 3 的键-值对

    user=> (subseq numbers >= 3)
    ([3 "three"] [4 "four"] [5 "five"])


    ; 过滤所有键小于 1 大于 4 的键-值对

    user=> (subseq numbers >= 2 <= 4)
    ([2 "two"] [3 "three"] [4 "four"])

    
    ; 过滤所有键小于 10 的键-值对，返回 nil

    user=> (subseq numbers >= 10)
    nil


rsubseq
-------------

| **(rsubseq sc test key)**
| **(rsubseq sc start-test start-key end-test end-key)**

用法和 `subseq`_ 一样，但是返回的序列是逆序排序的。

等同于执行 ``(rseq (subseq sc test key))`` 或者 ``(rseq (subseq sc start-test start-key end-test end-key))`` 。

::

    ; 测试数据

    user=> (def numbers (sorted-map 1 "one" 2 "two" 3 "three" 4 "four" 5 "five"))
    #'user/numbers

    user=> numbers
    {1 "one", 2 "two", 3 "three", 4 "four", 5 "five"}


    ; 过滤所有键小于 1 大于 4 的键-值对，并逆序地返回结果

    user=> (rsubseq numbers >= 2 <= 4)
    ([4 "four"] [3 "three"] [2 "two"])


    ; 过滤所有键小于 2 的键-值对，并逆序地返回结果

    user=> (rsubseq numbers > 2)
    ([5 "five"] [4 "four"] [3 "three"])



