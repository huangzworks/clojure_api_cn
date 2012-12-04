copy
=============

| **(copy input output & opts)**

把 ``input`` 的内容拷贝到 ``output`` ，成功返回 ``nil`` ，失败抛出 ``IOException`` 。

``input`` 可以是 ``java.io.InputStream`` ， ``java.io.Reader`` ， ``java.io.File`` ， ``byte`` 数组，或者 ``java.lang.String`` 。当输入是 ``java.lang.String`` 的时候，是把字符串本身拷贝到输出。

``output`` 可以是 ``java.io.OutputStream`` ， ``java.io.Writer`` 或者 ``java.io.File`` 。

``opts`` 可以包含 ``:buffer-size`` 和 ``encoding`` 。 ``:buffer-size`` 默认1024。

除了自己打开的， ``copy`` 不会关闭任何流。


::

    user> (use 'clojure.java.io)
    nil
    user> (copy "XXXXXX" (output-stream "/tmp/x"))
    nil
    user> (slurp "/tmp/x")
    "XXXXXX"
    user> (copy (file "/tmp/x") (output-stream "/tmp/xx"))
    nil
    user> (slurp "/tmp/x")
    "XXXXXX"
