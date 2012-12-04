as-relative-file
====================

| **(as-relative-path x)**

接受一个 ``x`` 参数，据此返回相对路径字符串。 ``x`` 的类型可以是 ``java.lang.String`` ， ``java.io.File`` ， ``java.net.URL`` 和 ``java.net.URI`` ，跟 ``as-file`` 一样。

如果 ``x`` 不是用相对路径表示的，则抛出 ``IllegalArgumentException`` 。

::

    user> (as-relative-path "./tmp")
    "./tmp"
    user> (as-relative-path "tmp")
    "tmp"
    user> (as-relative-path "/tmp")
    ;;IllegalArgumentException /tmp is not a relative path  clojure.java.io/as-relative-path (io.clj:404)
    user> (as-relative-path (java.io.File. "tmp-file"))
    "tmp-file"
