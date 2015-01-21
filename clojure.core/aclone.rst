aclone
--------

**(aclone array)**

返回Java数组的克隆，作用于已知类型的数组

::

    user=> (def a (int-array [1 2 3 4]))
    #'user/a

    user=> (def b (aclone a))
    #'user/b
    
    user=> (aset b 0 23)
    23
    
    user=> (vec b)
    [23 2 3 4]
    
    user=> (vec a)
    [1 2 3 4]
