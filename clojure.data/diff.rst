diff
---------------

**(diff a b)**

递归比较a和b，返回一个tuple 如
[只在a中出现的  只在b中出现的  a和b中共同出现的]

比较规则:
* a和b相等 返回[nil,nil,a]
* Map键值相同值不同
* Set无法比较
* 所有的序列都被视为索引的关联集合，结果以向量的类型返回
* 所有东西(包含string)都视为原子且平等比较

::

    (use 'clojure.data)
    (def uno {:same "same", :different "one"})
    (def dos {:same "same", :different "two", :onlyhere "whatever"})
    (diff uno dos)
    => ({:different "one"} {:onlyhere "whatever", :different "two"} {:same "same"})
    ;;  {different in uno} {     different or unique in dos       } {same in both}
    (diff {:a 1} {:a 1 :b 2})
    => (nil {:b 2} {:a 1})
    ;; the first contains nothing unique, but only the second contains :b
    ;; and both contain :a


    (diff [1 2 3] [5 9 3 2 3 7])              ;;=> [[1 2] [5 9 nil 2 3 7] [nil nil 3]]
    (diff (set [1 2 3]) (set [5 9 3 2 3 7]))  ;;=> [#{1}  #{7 9 5}        #{3 2}]


