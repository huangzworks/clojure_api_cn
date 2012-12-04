output-stream
==============

| **(output-stream x & opts)**

根据 ``x`` 创建 ``java.io.BufferedOutputStream`` 。

``x`` 可以是 ``java.io.BufferOutputStream`` ， ``java.io.OutputStream`` ， ``java.io.File`` ， ``java.net.URL`` ， ``java.net.URI`` ， ``java.lang.String`` ， ``java.net.Socket`` 。

当 ``x`` 是 ``java.lang.String`` 时，会先尝试把 ``x`` 解释成 ``java.net.URL`` ，如果失败，则是 ``java.io.File`` 。

当 ``x`` 是 ``java.net.URL`` 和 ``java.net.URI`` 时，协议必须是 ``file`` 。

``opt`` 定义创建选项，key可以是 ``:append`` 和 ``:encoding`` 。

::

    user> (use 'clojure.java.io)
    nil
    user> (input-stream (as-file "/tmp/x"))
    ;;#<BufferedInputStream java.io.BufferedInputStream@49160709>
    user> (input-stream (as-file "/tmp/x") :append true)
    ;;#<BufferedInputStream java.io.BufferedInputStream@7f6ce64e>
