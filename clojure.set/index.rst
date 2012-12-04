index
=========

| **(index xrel ks)**


``index`` 类似于 SQL 中的 ``group by`` 操作：它把 ``xrel`` 中的成员按 ``ks`` 中列举的 ``key`` 的值进行分组。

其中， ``xrel`` 和 ``ks`` 都是序列(sequence)。 ``xrel`` 的成员是一个个 ``map`` ， ``ks`` 的成员是用于分组的 ``key`` 。

``index`` 返回一个新 ``map`` ，新 ``map`` 的 ``key`` 是 ``ks`` 的成员作为 ``key`` 在 ``xrel`` 中每个 ``map`` 取到的不同值，新 ``map`` 的 ``value`` 是满足这些值的 ``xrel`` 中成员的集合。


::

    user> (use 'clojure.set)
    nil

    ;; 处理 set

    user> (def points #{{:x 0 :y 0} {:x 0 :y 1} {:x 1 :y 0}}) ;; 定义三个点
    #'user/points

    user> (index points [:x])       ;; group by x 坐标
    {{:x 1} #{{:y 0, :x 1}},
     {:x 0} #{{:y 1, :x 0} {:y 0, :x 0}}}

    user> (index points [:y :x])    ;; group by x 和 y 坐标
    {{:x 1, :y 0} #{{:y 0, :x 1}}, 
     {:x 0, :y 0} #{{:y 0, :x 0}},
     {:x 0, :y 1} #{{:y 1, :x 0}}}

    user> (index points [:z])       ;; group by 不存在的 z 坐标
    {{} #{{:y 1, :x 0} {:y 0, :x 0} {:y 0, :x 1}}}

    ;; 还可以处理 vector

    user> (def points-vec [{:x 0 :y 0} {:x 0 :y 1} {:x 1 :y 0}])
    #'user/points-vec

    user> (index points-vec [:x])   
    {{:x 1} #{{:y 0, :x 1}}, {:x 0} #{{:y 1, :x 0} {:y 0, :x 0}}}
