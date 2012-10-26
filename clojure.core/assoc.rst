assoc
--------

| **(assoc map key val)**
| **(assoc map key val & kvs)**

assoc 表示 associate 的意思。

``assoc`` 接受一个 Map ，还有一个或多个 ``key-val`` 对，
返回一个和传入 Map 类型相同的新 Map ，
除了原来传入 Map 已有的数据外，
新 Map 还包含传给 ``assoc`` 的那些 ``key-val`` 对。

当一个向量被应用到 ``assoc`` 函数时，
返回一个新向量，
新向量的索引下标（index） ``key`` 的值就是 ``val`` 。

注意索引下标必须 ``<= (count vector)`` 。

::

    user=> (assoc {} :Clojure "Rich")
    {:Clojure "Rich"}

    user=> (assoc {:Clojure "Rich"} :Clojure "Rich Hickey")     ; 如果有同名 key ，那么那么覆盖它
    {:Clojure "Rich Hickey"}

    user=> (assoc [1 2 3] 0 10086)
    [10086 2 3]

    user=> (assoc [1 2 3] 3 10086)          ; key 最大可以等于 (count vector)
    [1 2 3 10086]

    user=> (assoc [1 2 3] 10086 10086)      ; key 不能大于 (count vector)
    IndexOutOfBoundsException   clojure.lang.PersistentVector.assocN
    (PersistentVector.java:136)



