if-not
------------

| **(if-not test then)**
| **(if-not test then else)**

对 ``test`` 部分进行求值，如果结果为 ``false`` ，那么对 ``then`` 部分求值。

另一方面，如果 ``test`` 部分的求值结果为 ``true`` ，且 ``else`` 部分不为空，那么求值 ``else`` 部分；否则返回 ``nil`` 。

::

    user=> (if-not false :then-part :else-part)
    :then-part

    user=> (if-not true :then-part)
    nil

    user=> (if-not true :then-part :else-part)
    :else-part
