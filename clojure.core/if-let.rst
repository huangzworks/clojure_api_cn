if-let
--------

| **(if-let bindings then)**
| **(if-let bindings then else & oldform)**

| **bindings => binding-form test**

如果 ``test`` 为真，那么结合 ``binding-form`` 绑定，对 ``then`` 部分进行求值。

如果 ``test`` 为假，那么对 ``else`` 部分进行求值。

::

    user=> (defn sum-all-even-number [all-number]
               (if-let [all-even-number (filter even? all-number)]
                   (reduce + all-even-number)
                   0))
    #'user/sum-all-even-number

    user=> (sum-all-even-number [1 2 3 4 5 6 7 8 9])
    20  ; 2 + 4 + 6 + 8

    user=> (sum-all-even-number [1 3 5 7 9])
    0
