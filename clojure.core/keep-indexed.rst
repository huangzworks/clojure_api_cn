keep-indexed
-------------------

**(keep-indexed f coll)**

对于 ``coll`` 中的每个项 ``item`` ，
以及 ``item`` 对应的索引下标 ``index`` ，
``(keep-indexed f coll)`` 返回一个惰性序列，
序列中包含 ``(f index item)`` 除 ``nil`` 之外的所有计算结果。

因为带副作用的函数会返回与计算结果无关的虚假值，
因此，为了确保虚假值不会混进 ``keep-indexed`` 所生成的惰性序列中，
``f`` 必须是一个无副作用的函数。

::

    ; 返回 0 - 9 内所有排序位置(index)为偶数的数字

    user=> (keep-indexed #(if (even? %1) %2 nil) (range 10))
    (0 2 4 6 8)



