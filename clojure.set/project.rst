project
===========

| **(project xrel ks)**

对于 ``xrel`` 中的每个元素， ``project`` 的结果集合只包含那些 ``key`` 在 ``ks`` 里出现过的元素为成员。

换一种说法来讲就是：将 ``xrel`` 的成员投影到 ``ks`` 指定的维度上。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L71>`_

::

    user> (use 'clojure.set)
    nil

    user> (def points           ;; 定义三个三维空间的点
      #{{:x 1 :y 0 :z 1}
        {:x 0 :y 1 :z 1}
        {:x 1 :y 1 :z 0}}) 
    #'user/points

    user> (project points [:x]) ;; 投影到 x 轴上
    #{{:x 0} {:x 1}}            ;; 返回值是一个集合，所以计算结果中的两个 {:x 1} 只有一个被保留

    user> (project points [:x :y])
    #{{:y 1, :x 0} {:y 1, :x 1} {:y 0, :x 1}} ;; 投影到 x-y 平面上
