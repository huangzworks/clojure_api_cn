join
=============

| **(join xrel yrel)**
| **(join xrel yrel km)**

``join`` 类似于SQL中的join，对 ``xrel`` 和 ``yrel`` 做关联操作。

``xrel`` 和 ``yrel`` 是两个序列，序列的每个成员都是一个map，map的每个key-value对可以看做数据库表的字段以及对应的值。

如果提供了 ``km`` 参数，则按照 ``km`` 所列出的key进行join。

::

    user> (use 'clojure.set)
    nil
    user> (def students
            #{{:id 1 :name "Li Lei"}
              {:id 2 :name "Han Meimei"}}) ;; 学生信息
    #'user/students
    user> (def score
            #{{:id 1 :score 60}
              {:id 2 :score 99}}) ;; 学生成绩
    #'user/score
    user> (join students score) ;; 关联一下
    #{{:score 99, :name "Han Meimei", :id 2} {:score 60, :name "Li Lei", :id 1}}
    user> (def score-vec
             [{:id 1 :score 60}
              {:id 2 :score 99}])
    #'user/score
    user> (join students score-vec) ;; vector也可以
    #{{:score 99, :name "Han Meimei", :id 2} {:score 60, :name "Li Lei", :id 1}}
