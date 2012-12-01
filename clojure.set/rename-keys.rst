rename-keys
============

| **(rename-keys map kmap)**

把 ``map`` 中的 key 按照 ``kmap`` 提供的映射改名。

可以使用 ``array-map`` 类型的 ``kmap`` 来指定替换执行的顺序。

注意，替换可能造成 key 冲突，导致原来的 key-value 对被覆盖。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L77>`_

::

    user> (rename-keys {:id 1 :name "Li Lei"} {:id :new-id :name :new-name})
    {:new-id 1, :new-name "Li Lei"}

    ; 改名造成 key 冲突，旧的 {:b 2} 被覆盖

    user> (rename-keys {:a 1 :b 2} {:a :b})
    {:b 1}

    ; 通过 array-map 指定替换执行的顺序

    user> (rename-keys  {:a 1 :b 2 :c 3}  (array-map :a :tmp :b :a :tmp :b)) 
    {:b 1, :a 2, :c 3}
