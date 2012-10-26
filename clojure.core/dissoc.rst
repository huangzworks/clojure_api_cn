dissoc
----------

| **(dissoc map)**
| **(dissoc map key)**
| **(dissoc map key & keys)**

dissoc 表示 dissociate 的意思。

``dissoc`` 接受一个 Map ，以及任意个数的 ``key`` ，
返回一个和传入 Map 类型相同的新 Map ，
这个新 Map 不包含所有给定 ``key`` 的映射。

::

    user=> (dissoc {:clojure "Rich" :python "Guido"})                               ; 没有传入 key
    {:python "Guido", :clojure "Rich"}

    user=> (dissoc {:clojure "Rich" :python "Guido"} :python)                       ; 传入单个 key
    {:clojure "Rich"}

    user=> (dissoc {:clojure "Rich" :python "Guido"} :ruby)                         ; 传入一个不存在于 Map 的 key
    {:python "Guido", :clojure "Rich"}

    user=> (dissoc {:clojure "Rich" :python "Guido" :ruby "Matz"} :python :ruby)    ; 传入多个 key
    {:clojure "Rich"}


