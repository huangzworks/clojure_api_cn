make-reader
=================

| **(make-reader x opts)**

根据 ``x`` 创建一个 ``java.io.BufferedReader`` 。``x`` 可以是 ``java.io.InputStream`` ， ``java.io.File`` ， ``java.net.URL`` ， ``java.net.URI`` ， ``java.lang.String`` ， ``java.net.Socket`` ， ``byte`` 数组或者 ``char`` 数组 。

当 ``x`` 是 ``java.lang.String`` 时，会先尝试把 ``x`` 解释成 ``java.net.URL`` ，如果失败，则是 ``java.io.File`` 。

``opt`` 是一个map，定义选项，key可以是 ``:append`` 和 ``:encoding`` 。


::

    user> (use 'clojure.java.io)
    nil
    user> (make-reader "http://baidu.com" {})
    ;;#<BufferedReader java.io.BufferedReader@5994a1e9>
