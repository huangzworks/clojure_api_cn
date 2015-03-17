rsubseq
-------------

| **(rsubseq sc test key)**
| **(rsubseq sc start-test start-key end-test end-key)**

用法和 `subseq` 函数一样，但是返回的序列是逆序排序的。

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


