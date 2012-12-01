select
============

| **(select pred xset)**

返回 ``xset`` 中所有使 ``pred`` 为真的元素。

``select`` 和 ``clojure.core/filter`` 类似，只是 ``select`` 的输入和输出都是 ``set`` 。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L64>`_

::

    user=> (use 'clojure.set)
    nil

    user=> (select even? #{1 2 3 4 5})
    #{2 4}

    user=> (select even? [1 2 3 4 5]) ;; 只能是set
    ClassCastException clojure.lang.PersistentVector cannot be cast to clojure.lang.IPersistentSet  clojure.core/disj (core.clj:1420)
