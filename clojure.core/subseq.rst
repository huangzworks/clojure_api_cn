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
