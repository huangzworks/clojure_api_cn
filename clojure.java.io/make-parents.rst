make-parents
===============

| **(make-parents f & more)**

创建父目录，成功返回 ``true`` 。

``f`` 和 ``more`` 可以是 ``java.lang.String`` ， ``java.io.File`` ， ``java.net.URL`` 或者 ``java.net.URI`` 。


::

    user> (use 'clojure.java.io)
    user> (make-parents "/tmp/a/b/c/d") ;; 创建 /tmp/a/b/c/
    true
    user> (make-parents "/tmp/a/x/" "y" "z/") ;; 创建 /tmp/a/x/y
    true
