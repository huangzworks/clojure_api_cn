merge
--------

**(merge & maps)**

返回一个含有剩余项的map。
如果key在多个map中存在，后面的值（从左向右的顺序）会覆盖前面的值

::
    user=> (merge {:a 1 :b 2 :c 3} {:b 9 :d 4})
    {:d 4, :a 1, :b 9, :c 3}

    user=> (merge {:a 1 :b 2 :c 3} {:b 9 :d 4} {:b 8 :d 3})
    {:d 3, :c 3, :b 8, :a 1}
