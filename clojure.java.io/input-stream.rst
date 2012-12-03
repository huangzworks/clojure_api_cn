input-stream
==============

| **(input-stream x & opts)**


根据 ``x`` 创建一个 ``java.io.BufferedInputStream`` 。

``x`` 可以是 ``java.io.BufferedInputStream`` ， ``java.io.InputStream`` ， ``java.io.File`` ， ``java.net.URL`` ， ``java.net.URI`` ， ``java.lang.String`` ， ``java.net.Socket`` ， ``byte`` 数组或者 ``char`` 数组 。

当 ``x`` 是 ``java.lang.String`` 时，会先尝试把 ``x`` 解释成 ``java.net.URL`` ，如果失败，则是 ``java.io.File`` 。

``opts`` 定义创建选项，key可以是 ``:append`` 和 ``:encoding`` 。

::

    user> (use 'clojure.java.io)
    nil
    user> (input-stream (java.io.File. "/tmp/x"))
    ;;#<BufferedInputStream java.io.BufferedInputStream@21606a56>
    user> (input-stream (java.io.File. "/tmp/x") :append true)
    ;;#<BufferedInputStream java.io.BufferedInputStream@3e347b11>
