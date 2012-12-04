max-key
==========

| **(max-key f item1)**
| **(max-key f item1 item2)**
| **(max-key f item1 item2 & items)**

将函数 ``f`` 应用到所有给定元素上，其中 ``(f item)`` 值最大的那个 ``item`` 被返回。

``(f item)`` 的结果必须是数字值。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L4419>`_

::

    user=> (max-key count "abc" 
                          "abcd"
                          "a"
                          "abcdefg"
                          "aa")
    "abcdefg"

