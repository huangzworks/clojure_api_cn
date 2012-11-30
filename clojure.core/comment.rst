comment
==========

**(comment & body)**

忽略 ``body`` ，返回 ``nil`` 。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L4165>`_

::

    user=> (comment hello-clojure)
    nil

    user=> (comment "clojure!")
    nil

    user=> (defn msg []  
             (comment "nothing but a greeting message here")
             (println "hello"))
    #'user/msg

    user=> (msg)
    hello
    nil
