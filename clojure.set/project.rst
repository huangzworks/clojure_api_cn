project
===========

| **(project xrel ks)**

对于每个 ``xrel`` 的元素， ``project`` 取 ``ks`` 指定的key作为新的元素，加入结果集合。

说的帅一点：把 ``xrel`` 的成员投影到 ``ks`` 指定的维度上。

::

    user> (use 'clojure.set)
    nil
    user> (def points
      #{{:x 1 :y 0 :z 1}
        {:x 0 :y 1 :z 1}
        {:x 1 :y 1 :z 0}}) ;; 定义三个三维空间的点
    #'user/points
    user> (project points [:x]) ;; 投影到x轴上
    #{{:x 0} {:x 1}}
    user> (project points [:x :y])
    #{{:y 1, :x 0} {:y 1, :x 1} {:y 0, :x 1}} ;; 投影到x-y平面上
