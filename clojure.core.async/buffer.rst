buffer
---------------

**(buffer n)**

返回一个大小固定为n的buffer，当buffer满了的时候，put操作会阻塞

::

    user=> (def c (chan (buffer 3)))
    #'user/c
