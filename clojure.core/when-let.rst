when-let
--------------

| **(when-let bindings & body)**
| **bindings => binding-form test**

如果 ``test`` 的值 ``value`` 为真，那么结合 ``binding-form`` 绑定，对 ``body`` 进行求值。

::

    user=> (defn drop-one [coll]
               (when-let [s (seq coll)]
                   (rest s)))
    #'user/drop-one

    user=> (drop-one [1 2 3])
    (2 3)
