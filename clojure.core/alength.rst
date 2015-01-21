alength
--------

**(alength array)**

返回Java数组长度,作用于所有类型

::

    (def array (into-array Integer/TYPE [1 2 3 4 5]))
    #'user/array

    (alength array)
    5
