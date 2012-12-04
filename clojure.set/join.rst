join
=============

| **(join xrel yrel)**
| **(join xrel yrel km)**

``join`` 类似于 SQL 中的 ``join`` 操作：它对 ``xrel`` 和 ``yrel`` 做关联操作。

``xrel`` 和 ``yrel`` 是两个序列，序列的每个成员都是一个 ``map`` ， ``map`` 的每个 key-value 对可以看做数据库表的字段以及对应的值。

如果提供了 ``km`` 参数，则按照 ``km`` 所列出的 ``key`` 进行关联。

.. TODO: 添加一个设置 ``km`` 参数的例子

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L111>`_

::

    user> (use 'clojure.set)
    nil

    ;; 处理 set

    user> (def students             ;; 学生信息
            #{{:id 1 :name "Li Lei"}
              {:id 2 :name "Han Meimei"}}) 
    #'user/students

    user> (def score                ;; 学生成绩
            #{{:id 1 :score 60}
              {:id 2 :score 99}})   
    #'user/score

    user> (join students score)     ;; 关联信息和成绩
    #{{:score 99, :name "Han Meimei", :id 2} 
      {:score 60, :name "Li Lei", :id 1}}

    ;; 处理 vector

    user> (def score-vec
             [{:id 1 :score 60}
              {:id 2 :score 99}])
    #'user/score

    user> (join students score-vec)
    #{{:score 99, :name "Han Meimei", :id 2} 
      {:score 60, :name "Li Lei", :id 1}}
