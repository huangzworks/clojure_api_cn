blank?
-------

**(blank? s)**

如果 ``s`` 是 ``nil`` 、空字符串 ``""`` 或者只包含空白的字符串，那么返回 ``true`` 。

::

    user=> (clojure.string/blank? nil)
    true

    user=> (clojure.string/blank? "") 
    true

    user=> (clojure.string/blank? "    ")
    true

    user=> (clojure.string/blank? "hello world")
    false
