comp
-------

| **(comp)**
| **(comp f)**
| **(comp f g)**
| **(comp f g h)**
| **(comp f g h & other-functions)**

``comp`` 接受一系列函数作为输入，
返回一个匿名函数。

这个匿名函数接受可变数量的参数（variable number of args），
并按从右到左的顺序，
将传入的函数应用到参数中。

::

    user=> ((comp str double +) 3 3 3)  ; 以下两个表达等价
    "9.0"

    user=> (str (double (+ 3 3 3)))
    "9.0"


