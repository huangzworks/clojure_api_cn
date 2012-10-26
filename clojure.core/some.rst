some
------

**(some pred coll)**

返回 ``coll`` 中第一个满足条件 ``(pred x)`` 的值 ``x`` 。

如果 ``coll`` 中没有任何元素 ``x`` 能满足 ``(pred x)`` ，
返回 ``nil`` 。

将一个集合用作 ``pred`` 是 ``some`` 的一个惯用法：
比如说，
``(some #{:fred} coll)`` 在 ``:fred`` 存在于 ``coll`` 时返回 ``:fred`` ，
如果不存在，就返回 ``nil`` 。

::

    user=> (some #{:fred} [:fred :peter :jack])
    :fred

    user=> (some #{:mary} [:fred :peter :jack])
    nil

    user=> (some #(>= % 10) [1 3 5 7 9])            ; 查看是否有 >= 10 的值存在
    nil

    user=> (some #(>= % 5) [1 3 5 7 9])             ; 查看是否有 >= 5 的值存在
    true


