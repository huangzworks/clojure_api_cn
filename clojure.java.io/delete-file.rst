delete-file
==============

| **(delete-file f & [silently])**

删除文件 ``f`` 。如果有第二个参数，且为真值，则当文件不存在的时候，不抛出异常。

::

        user> (use 'clojure.java.io)
        nil
        user> (spit "/tmp/x" "123") ;; 创建一个文件，写入内容
        nil
        user> (slurp "/tmp/x") ;; 验证一下，已经存在
        "123"
        user> (delete-file "/tmp/x") ;; 删掉它
        true
        user> (slurp "/tmp/x") ;; 没有了
        ;;FileNotFoundException /tmp/x (No such file or directory)  java.io.FileInputStream.open (FileInputStream.java:-2)
        user> (delete-file "/tmp/x") ;; 抛异常
        ;;IOException Couldn't delete /tmp/x  clojure.java.io/delete-file (io.clj:425)
        user> (delete-file "/tmp/x" true) ;; 安静删除
        true
