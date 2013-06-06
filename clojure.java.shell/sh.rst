.. _sh:

sh 
==============

**(sh & args)**


传递给出的字符串到 ``Runtime.exec()`` 来启动一个子进程。

选项有：

- ``:in`` ：给出下列合法的输入源给 ``clojure.java.io/copy`` , 比如， ``InputStream`` , ``Reader`` , ``File`` , ``byte[]`` 或者 ``String`` , 来提供子进程的标准输入（stdin）。

- ``:in-enc`` ：给出一个字符串。作为字符的编码名（比如， ``UTF-8`` 或者 ``ISO-8859-1``\ ）来转换 ``:in`` 中给定的字符串的编码，默认是 ``UTF-8`` 。 如果 ``:in`` 给出的字节数组(byte array), 那么它不会被解码，这个选项会被忽略。

- ``:out-enc`` ：选项可以是一个 ``:bytes`` 或者一个 ``String`` ， 如果给出的是一个 ``String`` , 它会被当作一个字符编码的名字，（比如， ``UTF-8`` 或者 ``ISO-8859-1``\ ）来转换子进程的标准输出的字符串编码，如果给出的是 ``:bytes`` , 子进程的标准输出会被存储到一个字节数组返回，默认是 ``UTF-8`` 。

- ``:env`` ：用一个 map 重载进程的环境变量（env），如果你是一个受虐狂，你可以用一个 ``String[]`` 。

- ``:dir`` ：用一个 ``String``  或者  ``java.io.File``  重载进程工作目录（dir）

你可以用 ``with-sh-env`` 或者 ``with-sh-dir`` 绑定 ``:env`` 或者 ``:dir`` 到多个操作。

``sh`` 返回一个 map ：

- ``:exit`` ：子进程的返回码
- ``:out`` ：子进程的标准输出（stdout）（\ ``byte[]`` 或者 ``String``\ ）
- ``:err`` ：子进程的标准错误（stderr）（用平台默认的编码的 ``String``\ ）

`查看源码 <https://github.com/clojure/clojure/blob/fe0cfc71e6ec7b546066188c555b01dae0e368e8/src/clj/clojure/java/shell.clj#L79>`_

::


        user=> (use '[clojure.java.shell :only [sh]])

        ;; Note: The actual output you see from a command like this will look messier.
        ;; The output below has had all newline characters replaced with line
        ;; breaks.  You would see a big long string with \n characters in the middle.
        user=> (sh "ls" "-aul")

        {:exit 0, 
         :out "total 64
        drwxr-xr-x  11 zkim  staff    374 Jul  5 13:21 .
        drwxr-xr-x  25 zkim  staff    850 Jul  5 13:02 ..
        drwxr-xr-x  12 zkim  staff    408 Jul  5 13:02 .git
        -rw-r--r--   1 zkim  staff     13 Jul  5 13:02 .gitignore
        -rw-r--r--   1 zkim  staff  12638 Jul  5 13:02 LICENSE.html
        -rw-r--r--   1 zkim  staff   4092 Jul  5 13:02 README.md
        drwxr-xr-x   2 zkim  staff     68 Jul  5 13:15 classes
        drwxr-xr-x   5 zkim  staff    170 Jul  5 13:15 lib
        -rw-r--r--@  1 zkim  staff   3396 Jul  5 13:03 pom.xml
        -rw-r--r--@  1 zkim  staff    367 Jul  5 13:15 project.clj
        drwxr-xr-x   4 zkim  staff    136 Jul  5 13:15 src
        ", :err ""}


        user=> (use '[clojure.java.shell :only [sh]])

        user=> (println (:out (sh "cowsay" "Printing a command-line output")))

         _________________________________ 
        < Printing a command-line output. >
         --------------------------------- 
                \   ^__^
                 \  (oo)\_______
                    (__)\       )\/\
                        ||----w |
                        ||     ||

        nil             




        user=> (use '[clojure.java.shell :only [sh]])
        nil

        ;; note that the options, like :in, have to go at the end of arglist
        ;; advantage of piping-in thru stdin is less need for quoting/escaping
        user=> (println (:out (sh "cat" "-" :in "Printing input from stdin with funny chars like ' \" $@ & ")))
        Printing input from stdin with funny chars like ' " $@ & 
        nil   
