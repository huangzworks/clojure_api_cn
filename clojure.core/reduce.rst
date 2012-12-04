reduce
===========

| **(reduce f coll)**
| **(reduce f val coll)**

``reduce`` 的行为由以下情况定义：

- 没有给定 ``val`` ：
    - ``coll`` 为空：以无参数方式调用 ``f`` ，调用所得的值为返回值。
    - ``coll`` 只有一个元素：不调用 ``f`` ，直接将那个元素用作返回值。
    - ``coll`` 有多于一个元素：将 ``coll`` 的前两个元素应用到 ``f`` ，得到的结果再和 ``coll`` 的第三个元素一起应用到 ``f`` ，以此类推。
- 有给定 ``val`` ：
    - ``coll`` 为空：不调用 ``f`` ，直接返回 ``val`` 。
    - ``coll`` 不为空：将 ``val`` 和 ``coll`` 的第一个元素应用到 ``f`` ，得到的结果再和 ``coll`` 的第二个元素一起应用到 ``f`` ，以此类推。

``f`` 应该是一个接受两个参数的函数，如果处理的 ``coll`` 可能为空，那么它还应该能进行无参数调用。

`查看源码 <https://github.com/clojure/clojure/blob/d0c380d9809fd242bec688c7134e900f0bbedcac/src/clj/clojure/core.clj#L6016>`_

::

    user=> (reduce + [])            ; coll 为空， + 返回无参数调用结果 0
    0

    user=> (reduce + (range 10))    ; coll 不为空
    45

    user=> (reduce + 0 (range 10))  ; coll 不为空，且给定 val
    45

