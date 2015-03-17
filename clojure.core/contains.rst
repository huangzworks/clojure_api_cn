contains?
---------------

**(contains? coll key)**

如果 ``key`` 存在于给定 ``coll`` 中，
那么返回 ``true`` ，否则返回 ``false`` 。

对于那些使用数值索引（index）的 collection 、比如向量和 Java 数组来说，
``contains?`` 用于测试给定的数值 ``key`` 是否在索引的范围(range)之内。

``contains?`` 不是线性复杂度的操作，
它可以在常数或对数复杂度内完成。

如果要检查一个 ``coll`` 是否符合某个条件，可以使用 `some` 函数。

::

    user=> (contains? {:clojure "Rich"} :python)        ; 测试 Map
    false

    user=> (contains? {:clojure "Rich"} :clojure)
    true

    user=> (contains? [1 3 5 7 9] 3)                    ; 测试向量
    true

    user=> (contains? [1 3 5 7 9] 10086)
    false



