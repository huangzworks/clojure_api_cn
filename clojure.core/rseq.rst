rseq
---------

**(rseq rev)**

在常数时间内，返回 ``rev`` 的逆序序列。

``rev`` 只能是向量或者 sorted-map 。

``rev`` 为空时，返回 ``nil`` 。

::

    ; 空向量和空 sorted-map

    user=> (rseq [])
    nil

    user=> (rseq (sorted-map))
    nil


    ; 非空向量

    user=> (rseq [1 2 3])
    (3 2 1)


    ; 非空 sorted-map

    user=> (def alpha (sorted-map :a "apple" :b "boy" :c "cat"))
    #'user/alpha

    user=> alpha
    {:a "apple", :b "boy", :c "cat"}

    user=> (rseq alpha)
    ([:c "cat"] [:b "boy"] [:a "apple"])


    ; 一些不能处理的情况

    user=> (rseq (list 1 2 3))
    ClassCastException clojure.lang.PersistentList cannot be cast to clojure.lang.Reversible  clojure.core/rseq (core.clj:1480)

    user=> (rseq nil)
    NullPointerException   clojure.core/rseq (core.clj:1480)
