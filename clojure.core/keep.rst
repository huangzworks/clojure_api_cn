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
