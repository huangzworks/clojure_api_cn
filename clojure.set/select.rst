
select
============

| **(select pred xset)**

和 ``clojure.core/filter`` 类似，选择出 ``xset`` 中使 ``pred`` 为真的元素，但是输入和返回值都是set。


::

    user=> (use 'clojure.set)
    nil
    user=> (select even? #{1 2 3 4 5})
    #{2 4}
    user=> (select even? [1 2 3 4 5]) ;; 只能是set
    ClassCastException clojure.lang.PersistentVector cannot be cast to clojure.lang.IPersistentSet  clojure.core/disj (core.clj:1420)
