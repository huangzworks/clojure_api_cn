into
---------------

**(into to from)**
将from-coll中的所有元素合并至to-coll并返回结果
::

    user=> (into (sorted-map) [ [:a 1] [:c 3] [:b 2] ] )
    {:a 1, :b 2, :c 3}
    user=> (into (sorted-map) [ {:a 1} {:c 3} {:b 2} ] )
    {:a 1, :b 2, :c 3}
