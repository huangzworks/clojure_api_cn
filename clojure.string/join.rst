join
------

| **(join coll)**
| **(join separator coll)**

先使用 ``(seq coll)`` 将 ``coll`` 转换为序列，然后返回一个包含序列里所有元素的字符串。

多个元素之间以一个可选的 ``separator`` 分隔开。

::

    user=> (def fruit ["apple" "banana" "cherry"])
    #'user/fruit

    user=> (clojure.string/join fruit)
    "applebananacherry"

    user=> (clojure.string/join ", " fruit)
    "apple, banana, cherry"
