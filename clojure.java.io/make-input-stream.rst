make-input-stream
======================

| **(make-input-stream x opts)**

根据 ``x`` 创建一个 ``java.io.BufferedInputStream`` 。

``x`` 可以是 ``java.io.BufferedInputStream`` ， ``java.io.InputStream`` ， ``java.io.File`` ， ``java.net.URL`` ， ``java.net.URI`` ， ``java.lang.String`` ， ``java.net.Socket`` 或者 ``byte`` 数组。

当 ``x`` 是 ``java.lang.String`` 时，会先尝试把 ``x`` 解释成 ``java.net.URL`` ，如果失败，则是 ``java.io.File`` 。

``opt`` 是一个map，定义选项，key可以是 ``:append`` 和 ``:encoding`` 。


::

    user> (use 'clojure.java.io)
    nil
    user> (make-input-stream "/tmp/x" {})
    ;;#<BufferedInputStream java.io.BufferedInputStream@3a7aa9f6>
    user> (make-input-stream (java.io.File. "/tmp/x") {})
    ;;#<BufferedInputStream java.io.BufferedInputStream@df077d2>
    user> (make-input-stream (java.io.File. "/tmp/NO_SUCH_FILE") {})
    ;;FileNotFoundException /tmp/NO_SUCH_FILE (No such file or directory)  java.io.FileInputStream.open (FileInputStream.java:-2)
