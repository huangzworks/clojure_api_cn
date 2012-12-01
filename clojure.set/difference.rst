difference
=============

| **(difference s1)**
| **(difference s1 s2)**
| **(difference s1 s2 & sets)**

返回集合 ``s1`` 和其余给定集合之间的差。

当只有一个参数时，返回该参数。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L48>`_

::

    user> (use 'clojure.set)
    nil

    ; 单个集合

    user> (difference #{:a :b :c})
    #{:a :c :b}

    user> (let [s #{:a :b :c}] (identical? s (difference s)))
    true

    ; 两个集合

    user> (difference #{:a :b :c} #{:a :b})
    #{:c}

    user> (difference #{:a :b :c} #{:a :b :c})
    #{}

    ; 多个集合

    user> (difference #{:a :b :c} #{:a} #{:b})
    #{:c}
