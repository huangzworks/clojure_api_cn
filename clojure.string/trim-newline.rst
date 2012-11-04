trim-newline
----------------

**(trim-newline s)**

从字符串的末尾移除转行符 ``\n`` 和返回符 ``\r`` 。

类似于 Perl 的 ``chomp`` 函数。

::

    user=> (clojure.string/trim-newline "test")   
    "test"

    user=> (clojure.string/trim-newline "test\n")
    "test"

    user=> (clojure.string/trim-newline "test\r")
    "test"

    user=> (clojure.string/trim-newline "test\n\r")
    "test"

    user=> (clojure.string/trim-newline "test\r\n")
    "test"

    ; 只移除末尾的换行符

    user=> (clojure.string/trim-newline "leading newline\n trailing newline\n")
    "leading newline\n trailing newline"

