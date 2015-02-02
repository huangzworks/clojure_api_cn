zipmap
---------------

**(zipmap keys vals)**

返回一个含有键和相应值的map

::

    user=> (zipmap [:a :b :c :d :e] [1 2 3 4 5])
    {:e 5, :d 4, :c 3, :b 2, :a 1}
