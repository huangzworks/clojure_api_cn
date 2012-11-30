rename-keys
============

| **(rename-keys map kmap)**

把 ``map`` 中的key按照 ``kmap`` 提供的映射改名。
可以使用 ``array-map`` 类型的 ``kmap`` 来指定替换顺序。

注意，替换可能造成key冲突，导致原来的key-value对被覆盖。


::

    user> (rename-keys {:id 1 :name "Li Lei"} {:id :new-id :name :new-name})
    {:new-id 1, :new-name "Li Lei"}
    user> (rename-keys {:a 1 :b 2} {:a :b}) ;; 冲突了
    {:b 1}
    user> (rename-keys  {:a 1 :b 2 :c 3}  (array-map :a :tmp :b :a :tmp :b)) ;; 依赖array-map提供的替换顺序
    {:b 1, :a 2, :c 3}
