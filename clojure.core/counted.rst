counted?
--------------

**(counted? coll)**

如果 ``coll`` 实现了常数复杂度的 ``count`` 操作，那么返回 ``true`` 。

::

    ; 向量、列表、Map 和集合的 count 操作都是常数复杂度的
    ; 但字符串不是

    user=> (counted? [1 2 3])
    true

    user=> (counted? '(1 2 3))
    true

    user=> (counted? {:clojure "Rich"})
    true

    user=> (counted? #{:a :b :c})
    true

    user=> (counted? "string")
    false


