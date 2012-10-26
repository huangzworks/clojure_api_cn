partial
------------

| **(partial f arg1)**
| **(partial f arg1 arg2)**
| **(partial f arg1 arg2 arg3)**
| **(partial f arg1 arg2 arg3 & more)**

``partial`` 接受一个函数 ``f`` ，
以及少于正常 ``f`` 所接受参数数量的参数，
并返回一个匿名函数。

当这个匿名函数被调用时，
传给它的附加参数（additional args）会和之前给定的参数一起，
传给函数 ``f`` 。

::

    user=> (def three-times (partial * 3))
    #'user/three-times

    user=> (three-times 10)                     ; (* 3 10)
    30

    user=> (three-times 20)                     ; (* 3 20)
    60

    user=> (defn add-x-y-z [x y z]
               (+ x y z))
    #'user/add-x-y-z

    user=> (def add-y-z (partial add-x-y-z 0))  ; x = 0
    #'user/add-y-z

    user=> (def add-z (partial add-y-z 1))      ; y = 1
    #'user/add-z

    user=> (add-z 2)                            ; z = 2
    3                                           ; (+ 0 1 2)


