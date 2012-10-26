conj
--------

| **(conj coll x)**
| **(conj coll x & xs)**

``conj`` 的完整词义是 conjoin ，
表示『相连接』的意思，
它用于将元素和 collection 拼接起来。

需要注意的是，
根据 ``coll`` 的类型，
组合会发生在 ``coll`` 的不同地方，
也即是， 元素 ``x`` 可能会被加入到 ``coll`` 的最左边，也可能会被加入到最右边。

当 ``coll`` 等于 ``nil`` ，
也即是，执行 ``(conj nil item)`` 时，
结果为 ``(item)`` 。

::

    ; coll 为 nil

    user=> (conj nil 1)
    (1)


    ; 向量的组合在尾部进行

    user=> (conj [0 1 2] 3)
    [0 1 2 3]


    ; 列表的组合在头部进行

    user=> (conj (list 0 1 2) 3)
    (3 0 1 2)


    ; 处理多个元素的 conj 
    ; 注意向量和列表的结果之间的不同

    user=> (conj [0 1 2] 3 4 5)
    [0 1 2 3 4 5]

    user=> (conj (list 0 1 2) 3 4 5)
    (5 4 3 0 1 2)


