escape
-----------

**(escape s cmap)**

使用函数 ``cmap`` 对字符串 ``s`` 中的每个字符 ``ch`` 进行转义，并返回一个新字符串。

转义按照以下规则进行：

* 如果 ``(cmap ch)`` 返回 ``nil`` ，那么将 ``ch`` 添加到新字符串

* 如果 ``(cmap ch)`` 不为 ``nil`` ，那么将 ``(str (cmap ch))`` 添加到新字符串。

::

    user=> (clojure.string/escape "I want 1 < 2 as HTML, & other good things." {\< "&lt;" \> "&gt;" \& "&amp;"})
    "I want 1 &lt; 2 as HTML, &amp; other good things."

