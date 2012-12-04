map-invert
============


| **(map-invert m)**

反转一个 ``map`` ，将它原本的 ``value`` 映射为新 ``map`` 的 ``key`` ，原本的 ``key`` 映射为新 ``map`` 的 ``value`` 。

.. note:: 当多个 ``key`` 有同一个 ``value`` 时，新 ``map`` 只保留其中的一个作为 ``key`` 。

.. p.s. 为毛这个函数在 ``clojure.set`` 里头...

::

    user> (use 'clojure.set)
    nil

    user> (map-invert {:a 1 :b 2})
    {2 :b, 1 :a}

    user> (map-invert {:a 1 :b 2 :c 2}) ;; 两个 2 冲突，丢掉了 :c
    {2 :b, 1 :a}
