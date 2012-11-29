index
-------

| **(index xrel ks)**


``index`` 类似于SQL中的group by操作，它把 ``xrel`` 中的成员按 ``ks`` 中列举的key的值进行分组。

其中， ``xrel`` 和 ``ks`` 都是clojure序列(sequence)。 ``xrel`` 的成员是一个个map， ``ks`` 的成员是用于分组的key。

``index`` 返回一个map，map的key是 ``ks`` 的成员作为key在 ``xrel`` 中每个map取到的不同值，map的value是满足这些值的 ``xrel`` 中成员的集合。


::

    user> (use 'clojure.set)
    nil
    user> (def points #{{:x 0 :y 0} {:x 0 :y 1} {:x 1 :y 0}}) ;; 定义三个点
    #'user/points
    user> (index points [:x]) ;; group by x坐标
    {{:x 1} #{{:y 0, :x 1}}, {:x 0} #{{:y 1, :x 0} {:y 0, :x 0}}}
    user> (index points [:y :x]) ;; group by x和y坐标
    {{:x 1, :y 0} #{{:y 0, :x 1}}, {:x 0, :y 0} #{{:y 0, :x 0}}, {:x 0, :y 1} #{{:y 1, :x 0}}}
    user> (index points [:z]) ;; group by 不存在的z坐标
    {{} #{{:y 1, :x 0} {:y 0, :x 0} {:y 0, :x 1}}}
    user> (def points-vec [{:x 0 :y 0} {:x 0 :y 1} {:x 1 :y 0}])
    #'user/points-vec
    user> (index points-vec [:x]) ;; vector也可以
    {{:x 1} #{{:y 0, :x 1}}, {:x 0} #{{:y 1, :x 0} {:y 0, :x 0}}}
