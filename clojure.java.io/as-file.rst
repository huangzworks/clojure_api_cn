as-file
===============

| **(as-file x)**

接受一个 ``x`` 参数，返回一个 ``java.io.File`` 对象。 ``x`` 的类型可以是 ``java.lang.String`` ， ``java.io.File`` ， ``java.net.URL`` 和 ``java.net.URI`` 。

当 ``x`` 的类型是 ``java.net.URL`` 和 ``java.net.URI`` 时，协议必须是 ``file`` 。

当 ``x`` 是 ``nil`` 时，返回 ``nil`` 。



::

    user> (use 'clojure.java.io)
    nil
    user> (.exists (as-file "/tmp"))
    true
    user> (.exists (as-file (java.io.File. "/tmp")))
    true
    user> (.exists (as-file (java.net.URL. "file:///tmp")))
    true
    user> (.exists (as-file (java.net.URL. "http://www.google.com")))
    ;;IllegalArgumentException Not a file: http://www.google.com  clojure.java.io/fn--8210 (io.clj:67)
