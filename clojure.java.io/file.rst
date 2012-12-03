file
==========

| **(file arg)**
| **(file parent child)**
| **(file parent child & more)**

根据参数创建一个 ``java.io.File`` 对象。

如果只有一个参数 ``arg`` ，返回对应的 ``java.io.File`` 对象。

如果有多个参数，第一个参数 ``parent`` 作为根目录；后续参数作为每一层子目录或文件，且必须是用相对路径表示的。

``parent`` , ``child`` 和 ``more`` 类型可以是 ``java.lang.String`` ， ``java.io.File`` ， ``java.net.URL`` 或者 ``java.net.URI`` 。

::

        user> (use 'clojure.java.io)
        nil
        user> (file "/tmp")
        #<File /tmp>
        user> (file "/tmp" "a" "b")
        #<File /tmp/a/b>
        user> (file "/tmp" "a" (java.io.File. "../b"))
        #<File /tmp/a/../b>
        user> (file (java.net.URL. "file:///tmp") "a" (java.io.File. "../b"))
        #<File /tmp/a/../b>
