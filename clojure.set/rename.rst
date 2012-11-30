rename
===========

| **(rename xrel kmap)**

把 ``xrel`` 中的元素的key改名，新旧名字的映射由 ``kmap`` 提供。

::

    user> (use 'clojure.set)
    nil
    user> (def students
      #{{:id 1 :name "Li Lei"}
        {:id 2 :name "Han Meimei"}})
    #'user/students
    user> (rename students {:id :student-id})
    #{{:name "Han Meimei", :student-id 2} {:name "Li Lei", :student-id 1}}
