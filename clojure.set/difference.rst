difference
=============

| **(difference s1)**
| **(difference s1 s2)**
| **(difference s1 s2 & sets)**

计算集合的差，即返回 ``s1`` 除去其他集合中元素后的集合。

当只有一个参数时，返回该参数。

::

    user> (use 'clojure.set)
    nil

    user> (difference #{:a :b :c})
    #{:a :c :b}

    user> (difference #{:a :b :c} #{:a :b})
    #{:c}

    user> (difference #{:a :b :c} #{:a :b :c})
    #{}

    user> (difference #{:a :b :c} #{:a} #{:b})
    #{:c}

    user> (let [s #{:a :b :c}] (identical? s (difference s)))
    true
