capitalize
-----------

**(capitalize s)**

将字符串 ``s`` 的首个字符转换成大写，剩余的其他字符全部转换为小写。

::

    user=> (clojure.string/capitalize "hello world")
    "Hello world"

    user=> (clojure.string/capitalize "HELLO WORLD")
    "Hello world"

