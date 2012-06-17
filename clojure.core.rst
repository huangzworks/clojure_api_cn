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


iterate
--------

| **(iterate f x)**

返回一个惰性序列，
序列元素的值为 ``x`` 、 ``(f x)`` 、 ``(f (f x))`` 、 ``(f (f (f x)))`` ，
诸如此类。

函数 ``f`` 必须是无副作用的。

::

    ; 生成一个计算所有正整数的惰性序列

    user=> (def z (iterate inc 1))
    #'user/z


    ; 取出第一个和第二个正整数

    user=> (nth z 0)
    1

    user=> (nth z 1)
    2


    ; 取出前十个正整数

    user=> (take 10 z)
    (1 2 3 4 5 6 7 8 9 10)


repeat
----------

| **(repeat x)**
| **(repeat n x)**

返回一个包含 ``n`` 个 ``x`` 的惰性序列。

如果不指定 ``n`` ，那么值 ``x`` 可以被包含无限次。

::

    ; 定义一个包含 10 个 "hi" 的惰性序列

    user=> (def ten-hi (repeat 10 "hi"))
    #'user/ten-hi

    user=> ten-hi
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")


    ; 定义一个包含无限个 "hi" 的惰性序列

    user=> (def infinite-hi (repeat "hi"))
    #'user/infinite-hi

    user=> (take 10 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")

    user=> (take 20 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")


range
---------

| **(range)**
| **(range end)**
| **(range start end)**
| **(range start end step)**

返回一个惰性序列，
序列里包含从大于等于 ``start`` 到小于 ``end`` 
区间内的所有数字(``start <= numbers < end``)，
数字的步进以 ``step`` 指定。

默认情况下， ``start`` 为 ``0`` ， ``step`` 为 ``1`` ，而 ``end`` 则为无限。

::

    ; 不指定任何参数，返回一个包含所有非负整数的惰性序列
    ; 0, 1, 2, 3 ...

    user=> (take 3 (range))
    (0 1 2)

    user=> (take 10 (range))
    (0 1 2 3 4 5 6 7 8 9)


    ; 只指定 end 
    ; 返回大于等于 0 到小于 end 之内的所有整数

    user=> (range 5)
    (0 1 2 3 4)

    user=> (range 10)
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 和 end

    user=> (range 5 10)
    (5 6 7 8 9)

    user=> (range 0 10)   
    (0 1 2 3 4 5 6 7 8 9)


    ; 指定 start 、 end 和 step
    ; 第一个惰性序列计算 2 到 20 内的所有偶数
    ; 第二个惰性序列计算 1 到 20 内的所有奇数

    user=> (range 2 20 2)
    (2 4 6 8 10 12 14 16 18)

    user=> (range 1 20 2)
    (1 3 5 7 9 11 13 15 17 19)


keep
---------

**(keep f coll)**

对于 ``coll`` 中的每个项 ``item`` ，
``(keep f coll)`` 返回一个惰性序列，
序列包含 ``(f item)`` 除 ``nil`` 之外的所有计算结果。

因为带副作用的函数会返回与计算结果无关的虚假值，
因此，为了确保虚假值不会混进 ``keep`` 所生成的惰性序列中，
``f`` 必须是一个无副作用的函数。

::
    
    user=> (keep inc [1 2 3])
    (2 3 4)

    ; 将空的 collection 传给 seq 函数会返回 nil
    ; 可以根据这个性质来测试 keep 
    ; 看它是否真的会省略等于 nil 的值

    user=> (seq [])
    nil

    user=> (keep seq (list [1 2 3] [] [4 5 6]))
    ((1 2 3) (4 5 6))


distinct
----------

**(distinct coll)**

给定一个 ``coll`` ，返回一个无重复元素的惰性序列。

::

    ; 有重复元素的向量

    user=> (distinct [1 2 1 2])
    (1 2)

    
    ; 无重复元素的向量

    user=> (distinct [1 2 3 4])
    (1 2 3 4)


filter
--------

**(filter pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``true`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 过滤 0 - 9 中所有的奇数

    user=> (filter even? (range 10))
    (0 2 4 6 8)


    ; 过滤 0 - 9 中所有的偶数

    user=> (filter odd? (range 10))
    (1 3 5 7 9)


    ; 过滤 0 - 9 中所有小于 10086 的数，结果为空

    user=> (filter #(> % 10086) (range 10))
    ()


remove
----------

**(remove pred coll)**

返回一个惰性序列，
序列中包含 ``coll`` 里所有 ``(pred item)`` 测试结果为 ``false`` 的项。

``pred`` 必须是一个无副作用的函数。

::

    ; 删除 0 - 9 中的所有偶数

    user=> (remove even? (range 10))
    (1 3 5 7 9)


    ; 删除 0 - 9 中的所有奇数

    user=> (remove odd? (range 10))
    (0 2 4 6 8)


    ; 删除 0 - 9 中所有大于等于 0 的数字，结果为空

    user=> (remove #(>= % 0) (range 10)) 
    ()

