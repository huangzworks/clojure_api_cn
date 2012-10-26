repeat
----------

| **(repeat x)**
| **(repeat n x)**

返回一个包含 ``n`` 个 ``x`` 的惰性序列。

如果不指定 ``n`` ，那么值 ``x`` 可以被包含无限次。

::

    ; 定义一个包含 10 个 "hi" 的惰性序列

    user=> (def ten-hi (repeat 10 "hi"))
    #'user/ten-hi

    user=> ten-hi
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")


    ; 定义一个包含无限个 "hi" 的惰性序列

    user=> (def infinite-hi (repeat "hi"))
    #'user/infinite-hi

    user=> (take 10 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")

    user=> (take 20 infinite-hi)
    ("hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi" "hi")



