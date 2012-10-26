sort
-------

| **(sort coll)**
| **(sort comparator coll)**

返回对 ``coll`` 进行排序之后得到的序列。

如果不指定 ``comparator`` ，
那么默认使用 ``compare.`` ，
``comparator`` 必须实现 ``java.util.Comparator`` 。

::

    user=> (sort [4 2 1 3])
    (1 2 3 4)

    user=> (sort >= [4 2 1 3])
    (4 3 2 1)

    user=> (sort <= [4 2 1 3])
    (1 2 3 4)


