split-lines
----------------

**(split-lines s)**

在字符串 ``s`` 的 ``\n`` 或者 ``\r\n`` 处分割开。

::

    user=> (clojure.string/split-lines "hello\nmoto\r\nagain\r\n")
    ["hello" "moto" "again"]

    user=> (clojure.string/split-lines "no-new-lines")
    ["no-new-lines"]

    user=> (clojure.string/split-lines "")
    [""]

    user=> (clojure.string/split-lines nil)
    ;NullPointerException   java.util.regex.Matcher.getTextLength (Matcher.java:1234)
