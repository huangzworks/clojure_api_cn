rename
===========

| **(rename xrel kmap)**

把 ``xrel`` 中的元素的key改名，新旧名字的映射由 ``kmap`` 提供。

`查看源码 <https://github.com/clojure/clojure/blob/5ca0c1feb7f7260aad257e52f2ddb0d426e2db77/src/clj/clojure/set.clj#L89>`_

::

    user> (use 'clojure.set)
    nil

    user> (def students
      #{{:id 1 :name "Li Lei"}
        {:id 2 :name "Han Meimei"}})
    #'user/students

    user> (rename students {:id :student-id})
    #{{:name "Han Meimei", :student-id 2} {:name "Li Lei", :student-id 1}}
