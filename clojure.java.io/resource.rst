resource
================

| **(resource n)**
| **(resource n loader)**


是用 ``ClassLoader`` 加载资源文件，返回 ``java.net.URL`` 对象。如果找不到资源文件，返回 ``nil``。

``n`` 是资源名字字符串。 如果要使用特定的 ``ClassLoader`` ，需要使用 ``loader`` 参数。

::

    user> (use 'clojure.java.io)
    nil
    user> (resource "project.clj")
    #<URL jar:file:/Users/xiafei/.lein/self-installs/leiningen-2.0.0-preview10-standalone.jar!/project.clj>
