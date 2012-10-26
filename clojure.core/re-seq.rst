re-seq
-----------

**(re-seq re s)**

返回一个惰性序列，
序列里包含字符串 ``s`` 中所有匹配模式 ``re`` 的值，
匹配使用 ``java.util.regex.Matcher.find()`` 进行，
每个匹配值都经过 ``re-groups`` 处理。

::

    ; 查找字符串中的所有数字值

    user=> (re-seq #"[0-9]+" "abs123def345ghi567")
    ("123" "345" "567")
