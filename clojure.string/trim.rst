trim
-----

从字符串的两端移除空白。

::

    user=> (clojure.string/trim "clojure")
    "clojure"

    user=> (clojure.string/trim "    clojure    ")
    "clojure"

